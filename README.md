# Softis SPA (GitHub Pages ready)
- Single-file SPA (`index.html`) + `404.html` + `.nojekyll`.
- Hash routing. Live triangles + hover pull + smooth flip.
- Supabase reads `public.articles`.
SQL:
```
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
