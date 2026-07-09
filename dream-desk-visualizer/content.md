---
title: "Dream Desk Visualizer"
slug: dream-desk-visualizer
tagline: "Craft Your Comfort"
cardDescription: "Craft your comfort. Visualize your dream workspace in seconds."
coverImage: "assets/cover-dream-desk.svg"
coverAlt: "The Dream Desk Visualizer interface showing a Mid-Century themed office background, chair, desk, and laptop."
summary: "The Dream Desk Visualizer is an interior design application for your office space."
heroImage: "assets/mockup-hero-dream_desk.svg"
heroAlt: "The Dream Desk Visualizer allows users to personalize (select your dream background, desk, chair, and computer), share (save your custom image and send it to friends), and switch between light and dark modes."
externalUrl: "https://griffin-dream-desk-visualizer.netlify.app/"
role: "UX Designer & Full-Stack Developer"
timeline: "1 week · 2026"
tools: "React, TypeScript, CSS/Tailwind CSS, Figma Make, Cursor, Node.js/npm, Radix, Lucide, Motion, & Recharts"
team: "Solo independent project"
---

## Challenge
Individuals often feel overwhelmed when designing a personalized workspace, struggling to bridge the gap between imagination and reality when selecting furniture, accessories, and decor. The Dream Desk Visualizer was developed to address the following challenges:

**Overcoming Visualization Barriers:** Users often struggle to envision how different combinations of furniture, lighting, and textures will appear within a specific space.
 
**Curating a Personalized Aesthetic:** It’s difficult for users to mix and match design elements that perfectly complement their personal tastes, especially when interiors merge different styles, time periods, and characteristics. 

**Crafting Comfort and Calm:** Users need a risk-free environment to experiment with large, high-investment components like desks and monitors. The challenge was to create an interactive space where users can evaluate scale, comfort, and cohesion prior to making permanent purchasing decisions.   

<!-- theme: lavender -->

## Process
### Establishing the web application structure & basic elements

I began by creating a site map to establish the main architecture, global state dependencies, and bidirectional navigation, which allowed me to prioritize technical planning alongside UI design. 

**Figure 1.** Application site map
Insert: `dream-desk_site_map.png`

Next, I submitted the following prompt below to Figma Make and developed four main office background themes: 

-	Boho: includes rattan shelves, natural materials, textiles, macramé, fairy lights, and warm earth tones.
-	Dark academic: moody, library vibes with dark woods, candles, antique bookcases, and velvet textiles.
-	Mid-century modern: clean lines, minimalist storage, geometric accents, natural lighting, and abstract art.
-	Gamer Vibes: A modern aesthetic with neon lights, dark purple hues, ample space for multiple monitors, speakers, etc.

I also built out the select chair page, specifying the following user options, while leaving the the accessorize, summarize, and manage pages blank: 
-	A natural, light-colored wood desk
-	An ornate mahogany desk
-	A teak or walnut mid-century modern desk
-	A sitting/standing, modern desk with a headphone holder

I didn’t love the visual output in the live preview section of the page, but the site structure was accurate. I decided to export the code as a zip file and import my project folder into Cursor to save Figma Make credits. You can view the initial site structure here (please insert `https://griffin-desk-organizer-app.figma.site/`).

### Visual style development
The primary challenge in developing the Dream Desk Visualizer was enabling users to interactively assemble a personalized office space across multiple layers (background, desk, chair, and computer), while maintaining a high-fidelity, photorealistic aesthetic. To move away from the flat, CSS-generated background, I uploaded an example image I generated in Gemini as inspiration for my boho-inspired theme. I proceeded to do this with the remaining three themes, and the result was much better-quality visuals for the background layer.

Unfortunately, continuing to stack images in the live preview proved to be challenging. I experimented with using PNG files with transparent backgrounds, but I encountered issues with jagged edges, lighting, and sizing relative to other objects on the screen. Even after manually tweaking the object sizes in chairAssets.ts to fine-tune the CSS width, it proved unsuccessful, as placement was also a significant factor (for example, chairs must be partially tucked under the desk). 

**Figure 2. Design Iterations ** 
Insert a swipeable photo gallery: 

`figma-gamer-ex.png` - please add the caption: “An example of the gamer theme and modern standing desk using Figma’s flat, CSS-generated images.”
`figma-midcentury-ex.png` - please add the caption: “An example of the boho theme and light natural wood desk using Figma’s flat, CSS-generated images.”
`missing-legs.png` Please add “Early attempts to layer isolated desk assets resulted in significant rendering errors, including missing legs and 'floating' furniture.”
`desks_w_accessories.png` - please add the caption: “Additionally, stacking images using the live preview was unsuccessful, as shown by the boho office background bleeding into the mid-century modern setup.”
`desks_w_accessories2.png` - please add the caption: “Another attempt to layer disparate assets, resulting in poor chair-to-floor blending and distracting artifact leakage from the boho accessory set into the gamer background.”
`giant-chair.png` - please add the caption “A clear example of the scaling and perspective issues encountered during the initial layering phase, where independent assets failed to maintain proper proportions relative to the workspace.”
`giant-screen.png` - please add the caption “Another instance of scaling failure where the computer asset's dimensions were disproportionately large, illustrating the lack of control over perspective when using independent transparent overlays.”

Ultimately, I discovered that relying on Cursor to generate pre-composed, full-scene composite images was the most time-consuming, but also the most successful approach. 

### AI-assisted development
In Cursor, I started by checking for necessary dependencies and installing Node.js and npm. 

**Figure 3.** 
Insert: 
`figma-make-prompt.png`

<!-- theme: night -->
<!-- galleries: true -->

### Establishing the web application structure & basic elements

### **Photorealistic Integration:** Experience seamlessly integrated, full-scene images that avoid rendering errors such as jagged edges, difficulty blending, and unsightly artifacts.

### **Artful Combination:** Effortlessly mix and match pieces from diverse themes, ensuring that furniture, textures, and accessories blend harmoniously, regardless of the combination. 

### **Improved Confidence in Decision Making:** Enjoy the peace of mind that comes with a realistic, risk-free preview, allowing you to assess the cohesion of your design choices before committing to significant financial investments.

<!-- theme: lavender -->
<!-- features: true -->



### Visual style development


### AI assisted development

The primary challenge of developing the 'Dream Desk Visualizer' was allowing users to interactively assemble a personalized office space using multiple layers (background, desk, chair, and computer), while maintaining a high-fidelity, photorealistic aesthetic. 


<!-- theme: night -->
<!-- galleries: true -->

## Solution

### **Photorealistic Integration:** Experience seamlessly integrated, full-scene images that avoid rendering errors such as jagged edges, difficulty blending, and unsightly artifacts.

### **Artful Combination:** Effortlessly mix and match pieces from diverse themes, ensuring that furniture, textures, and accessories blend harmoniously, regardless of the combination. 

### **Improved Confidence in Decision Making:** Enjoy the peace of mind that comes with a realistic, risk-free preview, allowing you to assess the cohesion of your design choices before committing to significant financial investments.

<!-- theme: lavender -->
<!-- features: true -->

## Deployment

Explore the completed Dream Desk Visualizer below, which leverages pre-composed images to maintain high-quality while keeping the load times minimal.

Add an "Open published app" primary button (hero and deployment sections) that opens in a new tab to griffin-dream-desk-visualizer.netlify.app

## Reflection

The most critical lesson I learned was that using pre-composed full-scene composite images, while time-consuming while building, was worth it in the long run. The manual approach to incorporating PNG files with transparent backgrounds was more prone to error. In the future, I’d like to explore potential solutions for asset variance. While depth and blending improved with the integration of AI-generated images, a consistent asset library would allow for real-time customization while maintaining the same photorealistic quality. 


---

Available assets in `assets/`:
- `cover-dream-desk.svg` — homepage card cover
- `mockup-hero-dream_desk.svg` — hero mockup
- `home-page-no_choices.png` — home page before selections
- `home_page-dream-desk-data.png` — home page with data
- `academic-setup.png` — academic desk setup
- `boho-setup.png` — boho desk setup
- `boho-setup-step1.png` — boho setup step one
- `gamer-setup.png` — gamer desk setup
- `final_setup.png` — final exported setup
