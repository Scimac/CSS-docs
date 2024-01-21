## Final Project notes and learnings

1. First some boiler plate code, resetting the predefined margins -

   ```
    /* Pre-processor Reset */

    *,
    *::before,
    *::after {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        font-family: 'Roboto', sans-serif;
        font-size: 1.3rem;
    }

    img {
        max-width: 100%;
    }

    a, a:hover {
        text-decoration: none;
        word-break: unset;
        white-space: nowrap;
    }

    .container {
        width: clamp(700px, 100%, 1200px);
        display: flex;
        justify-content: center;
        margin: 0 auto;
        padding-inline: 1rem;
    }

    /* Pre-processor Reset */
    ```

2. Make smaller and smaller components. It helps when you have to write media queries.
3. Follow mobile first approach, build for mobile first and that is always scalable to larger screens. (I followed top down approach as the website was simple. It helped in media queries)
4. while writing media queries, Top down approach, write for max-width clamps - as they work for smaller screens but don't mess up bigger screens.
5. Try to make or get a wireframe. It makes development a lot easier.