# Softis SPA — GitHub Pages ready

Завантаж усі файли з цього архіву у **корінь** репозиторію та ввімкни GitHub Pages:
Settings → Pages → **Deploy from a branch** → Branch: `main` / Folder: `/ (root)`.

## Supabase
Уже підставлено:
- URL: `https://zobpfysopstuvvpdtgob.supabase.co`
- ANON KEY: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InpvYnBmeXNvcHN0dXZ2cGR0Z29iIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTg3MjM2MjIsImV4cCI6MjA3NDI5OTYyMn0._0G1I3VtwSVoDT93mPsAiRI4Yf66zFppaCqhhGQgSbw`

Storage: створи public bucket **images** для обкладинок.

### SQL
```sql
create table if not exists public.articles (
  id uuid primary key default gen_random_uuid(),
  title text not null,
  content text not null,
  excerpt text,
  image text,
  created_at timestamptz default now()
);
alter table public.articles enable row level security;
create policy "Public read" on public.articles for select using (true);
create policy "Anon insert" on public.articles for insert with check (true);
```
