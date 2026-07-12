---
title: "Color Contrast Validator"
slug: color-contrast-validator
tagline: "Accessibility Simplified."
cardDescription: "Color Contrast Validator. Accessibility simplified."
coverImage: "assets/color-contrast-new.png"
coverAlt: “The Color Contrast Validator is a WGAC testing app. A laptop shows the landing page of the app with the text color #000000 and background color #FFFFFF set as the default. The user can click on “Test Readability” to check for readability.”
summary: "The Color Contrast Validator tool provides users with a text color and background color field to select the color combination of their choice. The user can preview the text and test readability using WCAG contrast ratios to pass or fail, displaying the exact ratio."
heroImage: "assets/mockup_hero-color_contrast_validator.svg"
heroAlt: "The Color Contrast interface showing a text readability combination that passes with a contrast ratio of 6:18:1, which meets WCAG AA standards with a minimum of 4:5:1 contrast. Beside this is a second phone screen displaying a scenario in which the color contrast ratio fails, with a contrast of 2.63:1. The problem: Many designers struggle to quickly interpret complex WCAG compliance standards, leading to guesswork and increased cognitive load during the design process. The solution: By providing immediate, clear feedback on color contrast ratios, this tool simplifies decision-making, allowing designers to ensure accessibility without the mental fatigue of manual calculations."
externalUrl: "https://griffin-color-contrast-validator.netlify.app/"
role: "UX Designer & Full-Stack Developer"
timeline: "1 week · 2026"
tools: "Cursor, HTML, CSS, & JavaScript"
team: "Solo independent project"

---

## Overview

[TODO] Optional — omit if hero summary covers context.

## Challenge

An essential part of building web applications and websites is ensuring that designs are accessible. As a librarian, I’ve spent my career ensuring that information is accessible to everyone, regardless of their circumstances. When color contrast is poor, all users suffer, especially in bright sunlight or in high-glare environments. Digital spaces serve as gateways to countless services, from health care and education to managing finances and even communicating with loved ones. Yet, ensuring designs are accessible is often an afterthought. Accessibility isn’t just about compliance. It’s about usability and ensuring that all users, in all conditions, can access the resources they often desperately need. Moving into UX, I’m applying that same philosophy: making digital design inclusive, understandable, and accessible by default.

<!-- theme: lavender -->

## Process

###Establishing Color Contrast Validator Goals
Prior to starting my work in Cursor, I created a project folder and placed my index.html, script.js, and style.css folders inside. Because this was my first project using Cursor, I was very concerned about credit usage and consciously tried to be as efficient as possible when generating prompts. Before submitting my first prompt, I worked to identify the app’s main goals. In doing so, I developed the following outline: 

•	**Goal:** Create a single-page “Color Contrast Checker”
•	**Context:** Developed to help UX designers test color formats using hex codes to ensure accessibility compliance
•	**Constraints:** Implement a front-end design only, with no login, backend, or database logic
•	**Input:** Text prompt
•	**Output:** Layout of the app and initial execution of code (HTML, CSS, & JavaScript)
•	**Success Criteria:** A functional interface with text and background inputs that allow the user to enter the hex code, a submit button that calculates the minimum ratio for readability, and a “pass” or “fail” indicator.


###AI-assisted development
I provided Cursor with the prompt displayed below.

Please insert prompt1.png

The agent successfully met all requested criteria. I ran several tests to ensure that the ratios met industry standards, comparing other online hex code contrast tools against the initial build. Cursor also added a color selector overlay that lets the user preview the selected color by displaying the hex code in real time. The overlay allows the user to manually adjust the hue with a single click using a grid, spectrum, or slider view.

Everything was client-side only, or in other words, no backend, login, or database was needed, as requested. During testing, I realized the user needed an easy way to reset the input fields. I developed the following prompt next. 

Insert “prompt2.png”

I applied a couple of styling changes, but was happy, overall, with the user’s ability to restore the home page to a blank slate. I also noticed during the first iteration that the agent added a text readability box, which was clever. However, at some point, the box displayed only the background color, without the text. Because the component appeared as an empty box without text on top, it had the potential to confuse the user. I also felt that the empty contrast ratio, pass/fail status, and data tables appearing on the screen before the user had a chance to enter their values added visual clutter to the home page. As a direct result, I sent my next prompt. 

Please insert prompt3.png

I needed to reproduce the issue for testing, and Cursor added a neutral placeholder on load with real-time hex updates, with the results hidden until the Test Readability button was clicked. I was also concerned about the lack of feedback once the user submitted their hex codes. I decided to add a toast pop-up to confirm the user's action and give them the peace of mind that the information has been submitted. I prompted the cursor as displayed below.

Please insert prompt4.png

<!-- galleries: true -->

## Solution

## Solution
-	** The value of WCAG Contrast Compliance:** The app prioritizes universally accessible and efficient user experiences. By meeting WCAG standards, designers remove barriers for individuals with visual impairments, maintain readability in difficult environments, reduce cognitive load and eye strain, and ensure ethical and legal compliance. 

Please insert: need a picture with clear contrast in the frame.

-	**Reduced cognitive load: ** The user lands on a neutral landing page, with the most important action, the “Test Readability” button, highlighted in a bright blue. The default text color is #000000, with a background color of #FFFFFF. The “Sample text for readability” appears in the live preview section in a neutral, intuitive, static grey hue. 

Please insert: hompe-page.png (probably needs to live in a frame)

-	**Easier ways to select your codes:** The user can click the text box to easily enter or paste their hex code, or click the text color preview to access a grid, spectrum, or slider view that visually identifies the color of their choice.

Please insert: “IMG_9326.png”, “IMG_9237.png”, and “IMG 9328.png” (probably put inside cell phone frames, remove time and cellular data).

-	**Immediate visible feedback** The toast pop-up confirms the users’ actions once the information has been submitted, providing immediate confirmation that the app is evaluating the hex codes and feedback will be provided soon.

<!-- theme: lavender -->
<!-- features: true -->

## Deployment

Elevate your design standards by ensuring your text is readable for everyone. The Color Contrast Validator allows users to test text and background color combinations to ensure WCAG accessibility in seconds, helping build inclusive, high-contrast interfaces. 

## Reflection

Because I’ve previously incorporated various AI tools into my workflows, specifically for writing code, I was truly impressed by Cursor’s ability to respond to concise, deliberate prompts. I also realized that I needed to be extremely direct and specific with my needs, using Cursor’s select tool when available and opening the files I wanted to target. Additionally, I noticed that the quality of the agent's feedback declined when I was less deliberate in developing my prompts. One specific option I’d like to explore in the future is developing a “Nearest Accessible” color feature, ideally implementing an algorithm that calculates the nearest color that meets WCAG standards while keeping the color hue as close as possible to the user’s input. 

Please add a button that says “”: "https://griffin-color-contrast-validator.netlify.app/"