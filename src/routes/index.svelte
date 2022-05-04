<script context="module">
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

<pre>{JSON.stringify(projects, null, 2)}</pre>
