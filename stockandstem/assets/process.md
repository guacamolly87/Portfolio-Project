---
title: "Stock & Stem"
slug: stockandstem
tagline: "Thoughtfully planned. Perfectly plated."
cardDescription: "Plan, shop, and create for a stress-free kitchen."
coverImage: "assets/cover_stock&stem.svg"
coverAlt: "Stock and Stem project cover showing meal planning dashboard mockup"
summary: "Stock and Stem is a React-based recipe management and meal planning web application built with Supabase, Vite, and Tailwind CSS. It applies Human-Computer Interaction (HCI) principles and information architecture to reduce the cognitive load between the grocery list and the kitchen counter."
heroImage: "assets/mockup_hero-stock&stem-key_features.svg"
heroAlt: "Stock and Stem dashboard mockup highlighting weekly meal plan, pantry alerts, and grocery list"
role: "UX Designer & Full-Stack Development"
timeline: "8 weeks · 2026"
tools: "Figma, HTML/CSS, React, Supabase, Vite, Tailwind CSS, Cursor"
team: "Solo independent project"
---

## Overview

Home cooks juggle tight schedules and tight budgets. A weeknight stir-fry, a meal-prep Sunday, and a last-minute dinner guest all compete for the same bag of spinach before Wednesday. Most existing tools rely on enterprise-level inventory mindsets or messy, disconnected notes apps. 

Stock & Stem was built to explore what a dedicated meal planning and pantry tool looks like when it prioritizes user focus: fast to scan, accurate about what you have on hand, and structurally aligned with how people actually move through their week. 


## Challenge
<!-- theme: lavender.split | image: assets/cover_stock&stem.svg | imageAlt: Stock and Stem cover art with meal planning interface -->
Managing perishable groceries introduces a layer of micro-logistics that generic to-do apps ignore. Ingredients expire on different schedules, partial packages get opened mid-week, and fridge space is finite. 

When building the application, I targeted three core friction points in the typical home cooking workflow:

- **The Planning Fragmentation:** Recipes live in bookmarks, grocery lists live in notes apps, and real-time pantry inventory is a mystery until you open the fridge.
- **Delayed Visibility:** Discovering a missing ingredient usually happens when the pan is already hot instead of when a quick store run is still feasible.
- **Mental Overlap:** The system needs to bridge two distinct mental models: selecting recipes (inspiration) and auditing inventory (logistics).

The goal was to design a front-end interface that minimizes data-entry friction for someone interacting with a screen with intermittent attention and one hand on a spatula.

## Process
<!-- theme: night.split | image: assets/mockup_hero-stock&stem-key_features.svg | imageAlt: Stock and Stem key features mockup used during workflow mapping -->

As a solo developer applying HCI methodologies, I approached the project by mapping out a clean relational data model before writing code. I focused on translating real-world kitchen workflows into reactive state management.

By consolidating fragmented steps into centralized hubs, the interface reduces the cognitive load of switching back and forth between separate planning, shopping, and cooking tabs.

### Key Architectural & Design Priorities:

1.**Glanceable Hierarchy & Centralized Planning:** Critical signals—low stock, upcoming meals, expiring items—must be readable in under three seconds. This is achieved via a centralized calendar hub where users can view the day, edit schedules, pick meals, and trigger grocery generation natively in one screen.
2.**Zero-Friction State Toggles:** To accommodate active kitchen environments, tracking must be tactile and instant. The grocery view utilizes interactive checklists with toggle states to strike off items instantly as they are tossed into a physical cart.
3.**Low-Barrier Inventory Onboarding:** Instead of requiring manual text entry for every item, the system leverages an inventory system seeded with common pantry staples that can be rapidly tagged or untagged to accurately reflect real-world stock in seconds.


## Solution
<!-- theme: lavender.grid | image1: assets/mockup_hero-stock&stem-key_features.svg | image1Alt: Dashboard view with pantry alerts and weekly meal plan | image2: assets/cover_stock&stem.svg | image2Alt: Mobile-friendly grocery and recipe summary screen -->

The final concept centers on a **single weekly home view** that answers one question: *Can I cook what's on this week's plan without opening the fridge twice?*

### Key features

**Centralized Calendar Dashboard —** A unified, day-by-day planner that handles meal assignment, schedule adjustments, and grocery generation from a single, cohesive view, eliminating the need to jump between disconnected pages.

**Quick-Tag Pantry Inventory —** An inventory system pre-populated with common pantry staples. Users can effortlessly tag items they already own to instantly update their household stock levels.

**Interactive Grocery Checklists —** High-utility, actionable shopping lists featuring intuitive toggle interactions that let users cleanly strike items off as they shop or audit their kitchen.

**Smart Meal-Time Allocation —** Dedicated, clean layout blocks for Breakfast, Lunch, Dinner, and Snacks that display precise timing and meal states, ensuring the entire day is glanceable in under three seconds.

The interface stays on dark surfaces with lavender editorial panels for feature callouts—matching the portfolio design system—so dense information remains readable in a bright kitchen.

## Outcome
By applying Human-Computer Interaction (HCI) principles to reactive state management, Stock & Stem successfully translates complex kitchen micro-logistics into a zero-friction front-end interface. Consolidating the daily planning workflows into a single calendar view drastically reduced task fragmentation.

The live, responsive application achieves a "glanceable hierarchy," allowing home cooks to successfully manage their schedule, track meal prep progress, and audit inventory with intermittent attention and one hand on a spatula.

## Reflection

Consolidating the daily details taught me the value of aggressive layout simplification. In early site maps, I separated features into distinct sub-sections, but true user context demanded everything live on a single calendar axis.

If I continued the work, I would pilot offline-first sync for kitchens with spotty Wi-Fi and explore shared household views that shorten the "did we already buy this?" loop between partners. I'd also pressure-test accessibility under bright kitchen lighting and one-handed interaction—constraints that belong in the first sprint, not a polish pass.
