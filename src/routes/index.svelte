<script context="module">
import ProjectCard from '$lib/components/project-card.svelte'
  import {client} from "/lib/client.js";
	import { gql } from 'graphql-request';

		const query = gql`
			query GetProjects {
				projects {
					name
					slug
					description
					demo
					sourceCode
					image {
						url
					}
				}
			}
		`;

		const { projects } = await client.request(query);

		return { 
			props: { 
				projects
			}
		};
	};
</script>

<script>
	export let projects;
</script>

<h1>{JSON.stringify(projects, null, 2)}</h1>

<div>
	{#each projects as { name, slug, description, image }}
	  <ProjectCard {name} {description} url={image[0].url} {slug} />
	{/each}
  </div>