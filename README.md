# Next.js 15 Client-Side Navigation Bug

This repository demonstrates a subtle bug encountered in a Next.js 15 application involving client-side navigation and the `useEffect` hook.  The counter on the About page continues to increment even after navigating away from the page and returning. This is unexpected behavior and indicates a potential issue with how cleanup functions in `useEffect` are handled during client-side routing.

## Reproduction Steps

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm run dev` to start the development server.
4. Navigate to the `/about` page.
5. Observe the counter incrementing every second.
6. Navigate to the home page (`/`).
7. Navigate back to the `/about` page.
8. Notice that the counter continues to increment from where it left off, rather than restarting from 0.

## Potential Causes

The likely cause is an issue with the cleanup function within the `useEffect` hook.  While `clearInterval` is called, it might not be consistently executed or properly synchronized with the navigation process in Next.js 15's client-side routing.

## Solution

Check the `aboutSolution.js` file for a potential fix.