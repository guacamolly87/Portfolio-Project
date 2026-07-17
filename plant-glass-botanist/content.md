---
title: "Glass Botanist"
slug: plant-glass-botanist
tagline: "Keep your greens glowing."
cardDescription: "Plant care application that simplifies maintenance by categorizing plants and tracking their watering needs."
coverImage: "assets/cover-glass-botanist.svg"
coverAlt: "Glass botanist project cover"
summary: "The Glass Botanist is a centralized plant-care dashboard that tracks individual watering schedules based on specific plant categories to ensure optimal health. The app uses a visual health-status system to alert you to which plants need attention, helping you keep up through the use of timely reminders."
heroImage: "assets/mockup_hero-glass.png"
heroAlt: "The key features of the Glass Botanist include: plant management (add, update, and archive your plants while tracking your watering dates), health tracking (happy, neutral, and sad faces indicate when your plant requires care), and the leaf library, which enables you to customize your plant's care based on its watering needs"
externalUrl: "https://griffin-plant-glass-botanist.netlify.app/"
role: "UX Designer & Full-Stack Developer"
timeline: "2 weeks · 2026"
tools: "HTML/CSS, JavaScript, Tailwind CSS, Cursor, Lucid icons, Unsplash API, and Git/GitHub"
team: "Solo independent project"
---

## Challenge
Many plant owners only recognize the need for care after their plants exhibit clear signs of distress. Seasonal changes can affect plant health, including changes in temperature, sunlight levels, and humidity. Further compounding this issue is that the needs of one plant can vary significantly from the needs of another.

To address this, my goal became simplifying the cognitive burden of plant care by transforming the mundane chore of watering plants into an intuitive process that uses visual cues to encourage consistent routines.
<!-- theme: lavender -->

## Process
<!-- galleries: true -->

### Establishing the web application structure & basic elements
As a Memphis native and avid gardener of perennials, I am all too familiar with the unpleasant surprise of finding my thirsty hydrangeas wilting during the unforgiving summer months. I could easily empathize with this specific challenge, as I have personally spent many afternoons outside watering my plants after they have already started to protest, combating the humidity, swarming mosquitoes, and a leaking water hose that tends to spray everywhere.

However, because this was a two-week project, I decided to narrow my focus. I chose to focus on the habit of providing consistent care rather than the actual science behind plant care.

I began by establishing a site map comprised of four main pages: home (/), new (/new), my plants (/my_plants), and the leaf library (/library). I used Vibe coding to build out these sections.

**Figure 1.** Application site map
Insert: `site-map-plant-watering.png`

Next, I created relevant subsections that define the functions of each page. I mapped various user flows, including the quick watering function on the home page (/) and the ability to edit and archive existing plants within their collection.

**Figure 2.** Key user flows
Insert scrollable gallery with:
- `manage-plants-user-flow.png` — User flow for editing and archiving plants within a collection on the My Plants page.
- `quick-water_user-flow.png` — User flow for the quick watering function on the home page, enabling fast care updates with minimal taps.

Additionally, an attempt at narrowing my scope, I decided that the Leaf Library would be a way for the user to designate their plant into one of four categories:

- **Desert dweller** – low maintenance, prefers dry conditions; watering is needed every 14 – 17 days
- **Standard houseplant** – requires a consistent amount of moderate moisture; watering is needed every 7 days
- **Thirsty tropical** – prefers humid environments and damp soil; watering is needed every 3–5 days
- **Hydration heavy** – the soil should never be dry; water every 1–2 days

Additionally, I decided to integrate a getPlantHealthStatus function that determines the plant's facial expression, setting the criteria as follows:

- **Happy** – if the plant is within its recommended watering window
- **Neutral** – if the plant is at the end of its watering window
- **Distressed** – if the plant has exceeded its watering window

### Visual style development
Initially, I decided to use an earth-tone color scheme for all app pages (i.e., sage green, terracotta, warm browns, and creams). Unfortunately, I was unable to include the reactive faces based on plant health status to render correctly. The app could only show neutral and sad faces, so I left the feature out because it wasn't part of my initial MVP.

**Figure 3.** Initial launch home screen
Insert: `initial-launch-plant.png`

However, I was able to continue iterating later, refining my design and troubleshooting the getPlantHealthStatus function. I created a reusable skill, /inspire-design-system, to generate a Design.md folder. I reviewed various web applications on Dribbble and Landbook, and ultimately prompted Cursor to use the following site, https://hellopebl.com/?ref=land-book.com, as design inspiration. The following test file was generated.

**Figure 4.** Design system preview pages
Insert scrollable gallery with:
- `design1.png` — Coastal Enterprise Design System hero section with headline and call-to-action buttons
- `design2.png` — Design system color tokens and typography scale
- `design3.png` — Design system typography styles and spacing tokens
- `design4.png` — Design system buttons, tags, and content card components
- `design5.png` — Coastal Enterprise Design System hero section with partner logos
- `design6.png` — Design system color palette and typography tokens overview

I applied the new color palette and manually modified the plant icons because the new design clashed with the initial earth-tone color scheme. Please see the various iterations below.

**Figure 5.** Plant icon iterations
Insert scrollable gallery with:
- `plant1.png` — Early plant icon iteration for Glass Botanist
- `plant2.png` — Mid plant icon iteration for Glass Botanist
- `plant3.png` — Later plant icon iteration for Glass Botanist
- `plant4.png` — Final plant icon iteration for Glass Botanist

I was also able to restore the happy, neutral, and distressed faces to the pots at this time, ultimately discovering that the sad and happy mouths were too similar (Q28 24 vs Q28 25). Updating the PLANT_POT_EXPRESSIONS to happy (Q28 25) and sad (Q28 19) resolved the issue at last. Furthermore, I used Awaad to find a website with a liquid glass effect. I decided to apply this to my plant card containers.

### AI assisted development
I used Cursor to generate a my /inspire-design-system skill and DESIGN.md file. I also built the entire application by outlining the site map and key user flows, as well as troubleshooting the reactive expressions, and various designs.

**Figure 6.** Examples of AI assistance during the build process
Insert scrollable gallery with:
- `prompt-1new.png` — Cursor prompt to create the global /inspire-design-system skill
- `prompt2.png` — Cursor prompt defining preview phase constraints for DESIGN.md and preview.html
- `prompt3.png` — Cursor /inspire-design-system prompt with helopebl.com design inspiration URL
- `prompt4.png` — Cursor prompt to replace legacy CSS variables with the new Pacific palette
- `prompt6.png` — Cursor prompt to refine card styling with white surfaces and subtle borders
- `prompt7.png` — Cursor prompt to standardize plant icons with teal foliage and charcoal pots
- `prompt8.png` — Cursor prompt to adjust plant icon spacing and increase foliage size
- `prompt9.png` — Cursor prompt to add expressive pot faces based on watering status
- `prompt10.png` — Cursor prompt to connect face rendering logic to plant status data in plant-icons.js
- `prompt11.png` — Cursor prompt to apply sad CSS class to plant cards when status is overdue
- `prompt12.png` — Cursor follow-up on plant-pot--sad class applied but SVG still showing happy face
- `prompt13new.png` — Cursor prompt to apply liquid glass effect to plant card backgrounds
- `prompt14.png` — Cursor prompt to make dashboard and plant-grid containers transparent for liquid background glass effect
- `prompt15.png` — Cursor prompt to remove solid backgrounds on New Plant form and Plant Detail pages
- `prompt16.png` — Cursor prompt to update liquid-blob animation colors to Pacific theme palette

## Solution
<!-- theme: lavender -->

**How might we help new plant owners create consistent care habits by integrating gamified feedback?**

My app bridges the gap through a two-part design strategy that transforms plant care from a "chore to remember" into an intuitive, interactive experience:

1. **Educational clarity —** The app categorizes plants into four distinct watering tiers (Desert Dweller, Standard Houseplant, Thirsty Tropical, and Hydration Heavy), which helps remove the guesswork from care schedules.

**Figure 7.** Key screens across the app
Insert: `glass-botanist-phones.png`

2. **Gamification —** The app provides immediate, relatable emotional feedback through dynamic facial expressions (happy/neutral/distressed) to help users engage in an intuitive, interactive experience that promotes long-term plant care.

**Figure 8.** Finished app on iPad and iPhone
Insert: `glass-botanist-ipad.png`

This approach lowers the cognitive burden of plant maintenance, ensuring that the interface adapts to the user's reality in real-time, making consistent care an effortless part of their daily routine.

## Deployment
The Glass Botanist translates the anxiety of plant care into a low-friction, intuitive interface. Dynamic status modeling replaces reactive guesswork, allowing the user to interpret plant maintenance using clear, glanceable health indicators.

The live, responsive application prioritizes proactive habit formation, allowing new plant owners to manage care schedules, monitor moisture levels, and maintain overall plant health with minimal cognitive load.

Add "Open published app" primary button (hero and deployment sections) that opens in a new tab: https://griffin-plant-glass-botanist.netlify.app/

## Reflection
My work on the Glass Botanist highlights the transition from creating purely functional tools to designing for human behavior. I discovered that the most effective interfaces not only solve problems but also lessen the cognitive load of everyday life. This is achieved through state-driven design that adapts to the user's reality in real time.

In addition to individual plant tracking, the app provides a scalable framework. The categorization logic and visual health indicators can easily be expanded to include other care variables such as sunlight, fertilization, pruning, and repotting, ensuring that the design remains a robust, flexible tool that grows alongside the user's collection.

Available assets in `assets/`:
- `cover-glass-botanist.svg` — homepage card cover
- `mockup_hero-glass.png` — hero mockup
- `site-map-plant-watering.png` — application site map
- `manage-plants-user-flow.png` — user flow for plant management and archiving
- `quick-water_user-flow.png` — user flow for the quick water feature on the home page
- `initial-launch-plant.png` — initial home page at first launch with earth-tone color scheme
- `design1.png` — design system preview: hero section with headline and CTAs
- `design2.png` — design system preview: color tokens and typography scale
- `design3.png` — design system preview: typography styles and spacing tokens
- `design4.png` — design system preview: buttons, tags, and content card components
- `design5.png` — design system preview: hero section with partner logos
- `design6.png` — design system preview: color palette and typography overview
- `plant1.png` — early plant icon iteration
- `plant2.png` — mid plant icon iteration
- `plant3.png` — later plant icon iteration
- `plant4.png` — final plant icon iteration
- `prompt-1new.png` — Cursor prompt to create the /inspire-design-system skill
- `prompt2.png` — Cursor prompt defining preview phase constraints
- `prompt3.png` — Cursor prompt with helopebl.com design inspiration URL
- `prompt4.png` — Cursor prompt to replace legacy CSS variables with Pacific palette
- `prompt6.png` — Cursor prompt to refine card styling
- `prompt7.png` — Cursor prompt to standardize plant icons
- `prompt8.png` — Cursor prompt to adjust plant icon spacing
- `prompt9.png` — Cursor prompt to add expressive pot faces
- `prompt10.png` — Cursor prompt to connect face rendering to plant status data
- `prompt11.png` — Cursor prompt to apply sad CSS class when status is overdue
- `prompt12.png` — Cursor follow-up on plant-pot--sad class rendering issue
- `prompt13new.png` — Cursor prompt to apply liquid glass effect to plant cards
- `prompt14.png` — Cursor prompt to make dashboard and plant-grid containers transparent
- `prompt15.png` — Cursor prompt to remove solid backgrounds on New Plant and Plant Detail pages
- `prompt16.png` — Cursor prompt to update liquid-blob colors to Pacific theme palette
- `glass-botanist-phones.png` — key screens on iPhone (My Plants, New Plant, Home)
- `glass-botanist-ipad.png` — finished app on iPad and iPhone
- `leaf-library-lg.png` — leaf library screen
- `home_plant-glass-botanist.png` — home screen
- `my-plants-page.png` — my plants view
- `manage-plants.png` — plant management
- `New_plant.png` — add plant flow
- `Hompage-plant-glass-botanist-lg..png` — homepage layout
