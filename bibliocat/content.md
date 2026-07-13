---
title: "Bibliocat"
slug: bibliocat
tagline: "Book search and discovery for titles, authors, and covers."
cardDescription: "Book search and discovery for titles, authors, and covers."
coverImage: "assets/biblio-cover-new.png"
coverAlt: "Bibliocat project cover"
summary: "Fall down the rabbit hole of literature with Bibliocat, a book discovery tool powered by Open Library API. Search by title, author, or subject to find your next great adventure."
heroImage: "assets/mockup-hero-new-biblio.png"
heroAlt: "Bibliocat search results page showing a list of Dave Eggers books displayed under a 'Your Curious Collection' heading."
externalUrl: "https://bibliocat.netlify.app/"
role: "UX Designer & Full-Stack Developer"
timeline: "1 week · 2026"
tools: "React, Tailwind CSS, JavaScript, Figma, Flaticon, Netlify, Gemini, GitHub"
team: "Solo independent project"
---

## Challenge

The challenge when building Bibliocat was to design and build a book discovery tool that balances a cozy aesthetic with high-performance functionality, ensuring a seamless user experience across all interaction states, from the initial loading state to handling complex data errors.

<!-- theme: lavender -->

## Process

## Because I am a professional librarian, I jumped at the opportunity to build a book-searching application. In the library world, “biblio cat” stands for “bibliographic catalog.” I thought it would be the perfect name for my application because I wanted to create a rainy-day, cozy, cat-themed book-finding app. Initially, I walked through another set of prompts to lay the groundwork for the app, but I strongly disliked the color theme and style, so I decided to start over with a more clearly defined prompt.

Before generating my first prompt, I reviewed the Open Library API page to comply with usage guidelines and rate limits, and to understand the setup process for searching for authors, book titles, and book covers. 

## Visual Design
My initial design idea was to create a rainy-day, sleeping-cat-in-a-bookstore theme. I envisioned a design featuring a cat silhouette, with its paw hanging off the top edge of the search bar, giving the impression that it's lying on top of it. I could never get the sizing or placement quite right, so I decided to abandon the idea. This is how the original design appeared.

Please insert “early-iteration.png”

During my second project attempt, I asked Gemini to provide the hex codes for the book The Midnight Library by Matt Haig, as displayed below)

Please insert “the-midnight-library.jpg”

I envisioned a navy background with gold, orange, and teal accents. This was my first prompt for my second project attempt in Cursor.

Please insert “prompt1.png”, “prompt2.png”, and “homepage-early.png”
Please auto-generate captions.

I was much happier with the overall look of the web application. To ensure functionality, I tested various searches and noticed that users had to wait a few seconds for results to load. I decided to add a “loading” message and thought a cat silhouette prancing across the page would be fun, as if it were “searching the stacks.” While researching literary cat names, I discovered the Cheshire Cat from Alice’s Adventures in Wonderland, which felt like a perfect whimsical touch for my book-search app. 

**Loading State:** I implemented responsive indicators to maintain user engagement during asynchronous API calls, ensuring the interface remains interactive while data loads.
 
I developed the following prompt and sent it to Cursor.

Please insert “prompt3.png”

The design iterations for the loading status are displayed below.

Please insert “cat-themed loading” then “alice-themed-loading.png”, and finally “down-the-rabbit-hole.png” in a gallery box.

It was important for me to have paw print stamps throughout the theme to emulate footprints. This video showcases the loading state in action, featuring the custom paw-print animation.

<video width="100%" controls> <source src="./assets/loading-state-net.mp4" type="video/mp4"> Your browser does not support the video tag. </video>

**Empty State:** I also designed an intuitive “no result” message to guide users when searches retrieved no matching titles to help prevent confusion and encourage further exploration. 

Please insert “prompt4.png”.

Design iterations for the empty state.
Please insert a gallery box with the following photos: “library-quiet.png”, “oh-dear1.png”, and “oh-dear2.png”.

**Error State:** I implemented error handling to provide helpful feedback when network interruptions or API downtime occur, enabling users to retry their requests easily.

Please insert “prompt5.png”

Design iterations for the error state.
Please insert “error-state1.png” and “error-state2.png” in a gallery box.

**Success State:** I optimized the delivery and presentation of the search results, ensuring a seamless transition from the user’s query to displaying the actual results.

Please insert “prompt6.png”

Later iterations included the following: 
-	Adding a “Return to Home” button
Insert “prompt 7.png”

-	Creating credits for icons used from Flaticon
Insert “prompt8.png”

-	Reducing the size of the book cover images to make the search result appear sharper and less blurry
Insert “prompt9.png”

-	Adding the book publication year and edition number
Insert “prompt10.png”

-	Styling the home page
Insert “prompt11.png” in a gallery box, followed by “prompt12.png”, “prompt13.png”, “prompt14.png”, “homepage-early.png”, and “homepage-later.png”.

## AI-Assisted Development
UI & Experience Enhancements
-	**Quick Search Shortcuts:**
o	“**Surprise Me (Randomized):**” I added the ability for users to generate a random search from a curated array of classics to enable spontaneous discovery.
o	“**Featured Author (Static):**” This tool immediately filters or searches for works by Lewis Carroll, offering a one-click path to the primary author theme in the app.
o	**Browse Fantasy (Static):** Users can quickly execute a search for the fantasy genre, providing a quick shortcut for individuals interested in this category. 
Insert “prompt15.png”, “prompt16.png”, and “prompt17.png” in a gallery box.

Technical & Functional Updates
**Data Retrieval:** I enhanced the search function to include each book’s work key, enabling direct retrieval of detailed summaries from the Open Library API.
**Dynamic UI Updates:** I refactored the book component to fetch and display summaries automatically.

Insert “prompt 18.png” as a standalone image, directly underneath.


## Solution


### Reflection

Key features

Bibliocat was created to streamline the book-finding process while fostering a whimsical, thematic user experience through the following core features. 

-	**Intuitive Discovery:** Designed as a bibliographic catalog, the app uses Open Library API to provide a cozy book-finding experience that prioritizes discoverability and seamless access.
Insert image placeholder

-	**Integrate Summary Retrieval:** By capturing the unique work key for each search result, the application dynamically retrieves and displays detailed book descriptions to significantly enhance the user’s experience

Insert image placeholder
-	**Responsive UI Feedback:** Bibliocat captivates users with enchanting Alice-in-Wonderland-themed animations during loading states, ensuring the interface remains engaging and interactive while API calls are underway.

Insert image placeholder
-	**Quick Search Shortcuts** Easily discover your next favorite book by clicking on the “Surprise Me,” “Featured Author,” or “Fantasy” genre filters for a smooth, intuitive reading journey.

<!-- theme: lavender -->
<!-- features: true -->

## Deployment


The deployment provides users with an immersive, responsive, *Alice in Wonderland* themed search tool that integrates data from the Open Library API. The Bibliocat application is live on Netlify. 

Insert primary-button “Open published app”: https://bibliocat.netlify.app 


## Reflection

I most enjoyed moving beyond basic API integration to add themed loading states and consistent branding, which can create a more welcoming environment online. Technical hurdles, including creating a looping CSS animation for the pawprints during the loading state, enhanced my ability to use AI as a collaborator to resolve challenges. While I’m happy with the current version, future iterations could include more filtering options, such as limiting results by subject and genre. Furthermore, to enhance the enchanted *Alice in Wonderland* theme, I’d like to explore adding more animate imagery. For example, replacing the static teapot and teacup in the error state with a dynamic animation of tea being poured into a cup. 

Insert a secondary button: “Back to featured work”: https://molly-griffin.netlify.app/

