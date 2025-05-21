# Generate Dummy Pages

## Objective
Create all required static dummy pages based on the sitemap to simulate Google Tag Manager and Google Analytics tracking, following the project rules and analytics tracking plan.

---

## Requirements

### 1. Understand the Sitemap Structure
- Refer to the sitemap in `.github/instructions/sitemap.instructions.md`.
- Each unique page or page type must have a corresponding static component.
- Use the specified layout files for each page type.

### 2. Page & Component Mapping
- **Homepage**: Use `layout-homepage.md` → `<PageHomepage>`
- **Role Landing Pages** (Homeowner, Professional, Contractor): Use `layout-professional.md` → `<PageRoleHomeowner>`, `<PageRoleProfessional>`, `<PageRoleContractor>`
- **Product & Application**: Use `layout-product-and-application.md` → `<PageProductAndApplication>`
- **Brand/Product Pages**: Use `layout-product.md` → `<PageProductBrand>`
- **Project Inspiration**: Create a static component for the main page and for each project page if needed.
- **Project Segmentation**: Create static components for Residential, Commercial, Industrial, Institution & Others.
- **Resources & Support**
  - **Articles List**: Use `layout-list-article-news.md` → `<PageArticlesList>`
  - **Article Detail**: Use `layout-article-news.md` → `<PageArticleDetail>`
  - **E-Library**: Use `layout-e-library.md` → `<PageELibrary>`
- **Company**: Create static components for Company, News & Events, Careers.
- **About Us**: Create a static component.
- **Contact Us**: Use `layout-contact-us.md` → `<PageContactUs>`

### 3. Component Registration
- Register each static page component in Storyblok, matching the sitemap structure.
- For dynamic sections (e.g., Brand Pages, Article Pages), create generic static components for simulation.

### 4. Nuxt.js Routing
- Use the catch-all route (`pages/[...slug].vue`) to render the correct static component based on the URL.

### 5. Analytics Implementation Readiness
- Structure each component so analytics events can be easily triggered:
  - **Basic**: Page view, path, visit duration, bounce rate, user retention, demographics, referrals.
  - **Advanced**: Navigation flows (e.g., home → product), download clicks, scroll depth, contact form events, minimum visit duration.
- Ensure the role selection event is tracked on first visit.

### 6. Simulation Focus
- The site is for simulation only; no real data or backend integration is required.
- All pages/components should be static and ready for analytics event simulation.

---

## Deliverables

- Static components for all sitemap pages, using the correct layout.
- All components registered in Storyblok.
- Pages structured for easy analytics event simulation.
- Documentation of component mapping and analytics event points.

---

## Notes

- Follow the project rules in `.github/instructions/project-rules.instructions.md`.
- Refer to the analytics tracking plan in `.github/instructions/tracking-plan.instructions.md`.
- Ensure all dummy pages are ready for Google Tag Manager and Google Analytics simulation.