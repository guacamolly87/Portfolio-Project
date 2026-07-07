---
title: "Glass Botanist"
slug: plant-glass-botanist
tagline: "Keep your greens glowing."
cardDescription: "Plant care application that simplifies maintenance by categorizing plants and tracking their watering needs."
coverImage: "assets/cover-glass-botanist.svg"
coverAlt: "Glass botanist project cover"
summary: "The Glass Botanist is a centralized plant-care dashboard that tracks individual watering schedules based on specific plant categories to ensure optimal health. The app uses a visual health-status system to alert you which plants need attention, helping you keep through timely reminders."
heroImage: "assets/mockup_hero-plant-watering-app.svg"
heroAlt: "The key features of the Glass Botanist include: plant management (add, update, and archive your plants while tracking your watering dates), health tracking (happy, neutral, and sad faces indicate when your plant requires care), and the leaf library, which enables you to customize your plant's care based on its watering needs"
externalUrl: "griffin-plant-glass-botanist.netlify.app"
role: "UX Designer & Full-Stack Developer"
timeline: "2 weeks · 2026"
tools: "HTML/CSS, JavaScript, Tailwind CSS, Cursor, Lucid icons, and Unsplash API"
team: "Solo independent project"
---

## Challenge
Many plant owners only recognize the need for care after their plants exhibit clear signs of distress. Seasonal changes can affect plant health, including changes in temperature, sunlight levels, and humidity. Further compounding this issue is that the needs of one plant can vary significantly from the needs of another. 

To address this, my goal became simplifying the cognitive burden of plant care by transforming the mundane chore of watering plants into an intuitive process that uses visual cues to encourage consistent routines.
<!-- theme: lavender -->

## Process

###Establishing the Web Application Structure & Basic Elements
As a Memphis native and avid gardener of perennials, I am all too familiar with the unpleasant surprise of finding my thirsty hydrangeas wilting during the unforgiving summer months. I could easily empathize with this specific challenge, as I have personally spent many afternoons outside watering my plants after they have already started to protest, combating the humidity, swarming mosquitoes, and a leaking water hose that tends to spray everywhere. 

However, because this was a two-week project, I decided to narrow my focus. I chose to focus on the habit of providing consistent care rather than the actual science behind plant care. 

I began by establishing a site map comprised of four main pages: home (/), new (/new), my plants (/my_plants), and the leaf library (/library). I used Vibe coding to build out these sections. 

Insert: `site-map-plant watering.png`

Next, I created relevant subsections that define the functions of each page. I mapped various user flows, including the quick watering function on the home page (/) and the ability to edit and archive existing plants within their collection. 

Insert gallery box with:
`manage-plants-user-flow.png`
`quick-water_user-flow.png`

Additionally, an attempt at narrowing my scope, I decided that the Leaf Library would be a way for the user to designate their plant into one of four categories:

-	**Desert dweller** – low maintenance, prefers dry conditions; watering is needed every 14 – 17 days
-	**Standard houseplant** – requires a consistent amount of moderate moisture; watering is needed every 7 days
-	**Thirsty tropical** – prefers humid environments and damp soil; watering is needed every 3-5 days
-	**Hydration heavy** – the soil should never be dry; water every 1-2 days
Additionally, I decided to integrate a getPlantHealthStatus function that determines the plant’s facial expression, setting the criteria as follows: 

-	**Happy** - if the plant is within its recommended watering window
-	**Neutral** - if the plant is at the end of its watering window
-	**Distressed** - if the plant has exceeded its watering window

### Visual Style Development

Initially, I decided to use an earth-tone color scheme for all app pages (i.e., sage green, terracotta, warm browns, and creams). Unfortunately, I was unable to include the reactive faces based on plant health status to render correctly. The app could only show neutral and sad faces, so I left the feature out because it wasn’t part of my initial MVP. 

Insert `initial-launch-plant.png`

However, I was able to continue iterating later, refining my design and troubleshooting the getPlantHealthStatus function. I created a reusable skill, /inspire-design-system, to generate a Design.md folder. I reviewed various web applications on Dribbble and Landbook, and ultimately prompted Cursor to use the following site, https://hellopebl.com/?ref=land-book.com, as design inspiration. The following test file was generated.

Insert a scrollable gallery with the following images:
`test-page1.png`
`test-page2.png`
`test-page3.png`
`test-page4.png`

I applied the new color palette and manually modified the plant icons because the new design clashed with the initial earth-tone color scheme. Please see the various iterations below.

Insert a scrollable gallery with the following images:
`plant1.png`
`plant2.png`
`plant3.png`
`plant4.png`
`plant5.png`

I was also able to restore the happy, neutral, and distressed faces to the pots at this time, ultimately discovering that the sad and happy mouths were too similar (Q28 24 vs Q28 25). Updating the PLANT_POT_EXPRESSIONS to happy (Q28 25) and sad (Q28 19) resolved the issue at last. Furthermore, I used Awaad to find a website with a liquid glass effect. I decided to apply this to my plant card containers. 

### AI Assisted Development

I used Cursor to generate a my /inspire-design-system skill and DESIGN.md file. I also built the entire application by outlining the site map and key user flows, as well as troubleshooting the reactive expressions, and various designs. 

Insert a scrollable gallery with the following images:
``
``
``
``
<!-- theme: night -->
<!-- galleries: true -->

### Solution
**How might we help new plant owners create consistent care habits by integrating gamified feedback?**

Insert the following image:
`glass-botanist-phones.png`

My app bridges the gap through a two-part solution: 

1.	**Educational Clarity:** The app categorizes plants into four distinct watering tiers (Desert Dweller, Standard Houseplant, Thirsty Tropical, and Hydration Heavy), which helps remove the guesswork from care schedules. 
2.	**Gamification:** The app provides immediate, relatable emotional feedback through dynamic facial expressions (happy/neutral/distressed) to help users engage in an intuitive, interactive experience that promotes long-term plant care.

Insert the following image:
`glass-botanist-ipad.png`

<!-- theme: lavender -->
<!-- features: true -->

### Deployment
The Glass Botanist translates the anxiety of plant care into a low-friction, intuitive interface. Dynamic status modeling replaces reactive guesswork, allowing the user to interpret plant maintenance using clear, glanceable health indicators. 

The live, responsive application prioritizes proactive habit formation, allowing new plant owners to manage care schedules, monitor moisture levels, and maintain overall plant health with minimal cognitive load.

Add "Open Published App" primary-button that opens in a new tab and takes the user to: https://griffin-plant-glass-botanist.netlify.app/

### Reflection
My work on the Glass Botanist highlights the transition from creating purely functional tools to designing for human behavior. I discovered that the most effective interfaces not only solve problems but also lessen the cognitive load of everyday life. This is achieved through state-driven design that adapts to the user's reality in real time.

Available assets in `assets/`:
- `glass-botanist-ipad.png` - image of the finished app on an ipad and iphone
- `glass-botanist-iphones.png` - image on the my plants, new plant, and home page screens on an iphne
- `mockup_hero-plant-watering-app.svg` — hero mockup
- `home_plant-glass-botanist.png` — home screen
- `my-plants-page.png` — my plants view
- `manage-plants.png` — plant management
- `manage-plants-user-flow.png` - user flow for plant management
- `quick-water_user-flow.png` - user flow for the quick water feature on the home page
- `initial-launch-plant.png` - initial home page for when the app was first lauched
- `site-map-plant-watering.png` - site map for the Glass Botanist app
- `leaf-library-lg.png` — leaf library
- `New_plant.png` — add plant flow
- `Hompage-plant-glass-botanist-lg..png` — homepage layout
- `test-page1.png` - Example of Design test site page one
- `test-page2.png` - Example of Design test site page two
- `test-page3.png` - Example of Design test site page three
- `test-page4.png` - Example of Design test site page four
- `plant1.png` - Example of early plants iteration
- `plant2.png` - Example of mid plants iteration
- `plant3.png` - Example of later plants iteration
- `plant4.png` - Example of later plants iteration