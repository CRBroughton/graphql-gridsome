# GraphQL Demo

This project shows a simple demonstration of [GraphQL](https://graphql.org/) and [Vue](https://vuejs.org/) (built with [Gridsome](https://gridsome.org/) and [Tailwind](https://tailwindcss.com/)).

The project relies on GraphQL to fetch image URLS, article URLS and the year of the mission.

Those details are then passed to their relevant children components as props.

Clicking on any of the images shows a popup that details the above, with a clickable article link for the relevant mission.

Below you can find the Graphql api that was used for this project:

[http://api.spacex.land/graphql](http://api.spacex.land/graphql)