# README

https://evilmartians.com/chronicles/inertiajs-in-rails-a-new-era-of-effortless-integration

1. `rails new inertia_rails_example --skip-js -a propshaft -d postgresql`.
2. `bundle add vite_rails && bundle exec vite install`.
3. `npm i -D tailwindcss postcss autoprefixer && npx tailwindcss init -p`.
4. Update `tailwind.config.js`:
```
module.exports = {
  content: [
    './public/*.html',
    './app/helpers/**/*.rb',
    './app/frontend/**/*.{js,jsx,ts,tsx,svelte,vue}',
    './app/views/**/*.{erb,haml,html,slim}'
  ],
  variants: {
    extend: {},
  },
  plugins: [],
}
```
5. Create `app/javascript/entrypoints/application.css:`
```
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
```
5. Add `<%= vite_stylesheet_tag 'application' %>` to `app/views/layouts/application.html.erb`.

6. Integrate intertia
```
bundle add inertia_rails-contrib
bin/rails generate inertia:install
```