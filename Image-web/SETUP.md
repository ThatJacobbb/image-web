# Turning on sign-in and cloud sync (one-time, about 10 minutes)

Sign-in needs a small online database. This uses Supabase, which has a free plan. Without this setup the site still works fully; only the Account menu stays switched off.

1. Go to https://supabase.com, create a free account, and click **New project** (any name; save the database password somewhere).
2. When the project is ready, open **Authentication > URL Configuration**. Set **Site URL** to your GitHub Pages address (for example `https://yourname.github.io/image-web/`) and add the same address under **Redirect URLs**.
3. Open **SQL Editor**, paste this, and click **Run**:

```sql
insert into storage.buckets (id, name, public) values ('webs', 'webs', false) on conflict do nothing;
create policy "own web read" on storage.objects for select to authenticated
  using (bucket_id = 'webs' and (storage.foldername(name))[1] = auth.uid()::text);
create policy "own web insert" on storage.objects for insert to authenticated
  with check (bucket_id = 'webs' and (storage.foldername(name))[1] = auth.uid()::text);
create policy "own web update" on storage.objects for update to authenticated
  using (bucket_id = 'webs' and (storage.foldername(name))[1] = auth.uid()::text)
  with check (bucket_id = 'webs' and (storage.foldername(name))[1] = auth.uid()::text);
```

4. Open **Project Settings > API**. Copy the **Project URL** and the **anon public** key.
5. In `index.html`, find the line `const SB={url:'',key:''};` near the very end and paste them between the quotes. The anon key is meant to be public; the rules above make each person's saved web readable only by them.
6. Upload the changed `index.html` to GitHub again.

## Using it
Open **Account**, enter your email, and click the link in the email on the same device. Then use **Save to cloud** on one device and **Load from cloud** on another. Each account holds one web, and saving overwrites the previous cloud copy. Files over 50 MB (Supabase free plan) can't be saved, so very large webs still need Export/Import.

Supabase's built-in email sending is limited to a few messages per hour on the free plan. If you hit that, wait a bit or add your own email provider under Authentication > SMTP.
