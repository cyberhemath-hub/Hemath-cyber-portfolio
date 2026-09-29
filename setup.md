# Portfolio Setup Guide

Cybersecurity portfolio built with React, TypeScript, Vite, Tailwind CSS, Framer Motion, and Lucide React.

## 1. Requirements

- Node.js 18 or newer (check with `node -v`)
- npm (comes with Node.js)
- Git (for pushing to GitHub)

## 2. Install and run

```bash
unzip security-portfolio.zip
cd portfolio
npm install
npm run dev
```

Open the local URL that Vite prints (usually http://localhost:5173).

## 3. Useful commands

| Command | What it does |
| --- | --- |
| `npm run dev` | Start the dev server with hot reload |
| `npm run build` | Type-check with TypeScript and build to `dist/` |
| `npm run preview` | Serve the production build locally |

## 4. Project structure

```
src/
├── components/     UI components (Navbar, Hero, Services, Projects, ...)
├── data/           All editable content
│   ├── site.ts             Name, contact links, nav, skills
│   ├── services.ts         The three service cards
│   ├── projects.ts         Project cards and case studies
│   └── certifications.ts   Certificates (empty until you add some)
├── App.tsx
├── main.tsx
└── index.css       Tailwind import and colour theme
```

You only need to edit files in `src/data/` and `index.html` to make the site yours.

## 5. Replace the placeholders

### Personal details: `src/data/site.ts`

- `name`: your full name
- `email`, `linkedin`, `github`: your real links
- `skills`: delete anything you do not actually know or use

### Projects: `src/data/projects.ts`

- Replace every `[Placeholder]` line with content from your own reports and project documentation.
- Only list vulnerabilities and results that your documentation confirms.
- Do not include client names, private IP addresses, credentials, or tokens.
- Do not claim AI, LLM, or automated exploitation features unless your tool really has them.

### Certifications: `src/data/certifications.ts`

Add real certificates only:

```ts
{
  name: 'Course name',
  issuer: 'Issuing organization',
  date: 'Mon YYYY',
  category: 'Cybersecurity',
  type: 'Certification',            // or 'Professional Training'
  link: 'https://credential-url',   // optional
},
```

### SEO: `index.html`

- Replace `[Your Name]` in the `<title>` and Open Graph tags.
- Update the description if you like.
- Swap the inline favicon for your own file in a `public/` folder.

## 6. Contact form

The form validates in the browser (name, email, subject, message).

- **Without a backend:** submitting opens the visitor's email app with the message filled in, addressed to the `email` in `site.ts`.
- **With a form service** (Formspree, Getform, etc.): create a `.env` file in the project root:

```
VITE_FORM_ENDPOINT=https://your-form-service-url
```

Restart `npm run dev` after creating or changing `.env`.

## 7. Push to GitHub

Create an empty repository named `Hemath-cyber-portfolio` on GitHub (no README or .gitignore), then run:

```bash
printf "node_modules\ndist\n.env\n.env.local\n" > .gitignore
git init -b main
git add .
git commit -m "Initial commit: cybersecurity portfolio"
git remote add origin https://github.com/<your-username>/Hemath-cyber-portfolio.git
git push -u origin main
```

If GitHub asks for a password, use a personal access token instead.

## 8. Deploy (optional)

**Vercel or Netlify**

1. Import the GitHub repository.
2. Build command: `npm run build`
3. Output directory: `dist`
4. If you use the contact form endpoint, add `VITE_FORM_ENDPOINT` as an environment variable.

**GitHub Pages**

1. In `vite.config.ts`, add `base: '/Hemath-cyber-portfolio/'` inside `defineConfig({...})`.
2. Build with `npm run build` and publish the `dist/` folder (for example with a GitHub Actions workflow or the `gh-pages` package).

## 9. Before you share it

- [ ] Name, email, LinkedIn, and GitHub links replaced
- [ ] Every `[Placeholder]` in `projects.ts` replaced or removed
- [ ] Certifications added (or section left as-is)
- [ ] Unused skills removed
- [ ] Page title and Open Graph tags updated in `index.html`
- [ ] No confidential internship or client information anywhere
- [ ] `npm run build` completes without errors
- [ ] Checked on a phone-sized screen

## 10. Troubleshooting

- **Blank page or import errors:** delete `node_modules`, run `npm install` again.
- **Form endpoint not working:** confirm the variable name is exactly `VITE_FORM_ENDPOINT` and restart the dev server.
- **Type errors on build:** run `npm run build` and fix the file it names; the messages point to the line.
