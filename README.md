# anshumans-mastra

A [Mastra](https://mastra.ai/) project that deploys AI agents to [Vercel](https://vercel.com) using the Mastra Vercel deployer. It includes a weather agent powered by OpenAI's GPT-4o via the [Vercel AI Gateway](https://vercel.com/docs/ai-gateway).

## Weather Agent

The weather agent (`src/mastra/agents/weather-agent.ts`) fetches current weather data for any location and can suggest activities based on conditions. It uses the `vercel/openai/gpt-4o` model through the Vercel AI Gateway, which provides unified access to multiple AI providers with built-in observability, caching, and rate limiting.

## Getting Started

Start the development server:

```shell
pnpm run dev
```

Open [http://localhost:4111](http://localhost:4111) in your browser to access [Mastra Studio](https://mastra.ai/docs/getting-started/studio). It provides an interactive UI for building and testing your agents, along with a REST API that exposes your Mastra application as a local service.

You can start editing files inside the `src/mastra` directory. The development server will automatically reload whenever you make changes.

## Deployment to Vercel

This project uses the [`@mastra/deployer-vercel`](https://mastra.ai/guides/deployment/vercel) package to deploy to Vercel as a serverless application. The deployer is configured in `src/mastra/index.ts`:

```ts
import { VercelDeployer } from '@mastra/deployer-vercel';

export const mastra = new Mastra({
  // ...
  deployer: new VercelDeployer({ studio: true }),
});
```

To build for Vercel:

```shell
pnpm run build
```

**Note:** This project currently uses a local `.tgz` build of `@mastra/deployer-vercel` because studio support for Vercel deployments is not yet released. Once [mastra-ai/mastra#13532](https://github.com/mastra-ai/mastra/pull/13532) is merged and published, this project should switch to the published npm package instead.

For full deployment instructions, see the [Mastra Vercel deployment guide](https://mastra.ai/guides/deployment/vercel).

## Learn more

To learn more about Mastra, visit the [documentation](https://mastra.ai/docs/). This project includes example code for [agents](https://mastra.ai/docs/agents/overview), [tools](https://mastra.ai/docs/agents/using-tools), [workflows](https://mastra.ai/docs/workflows/overview), [scorers](https://mastra.ai/docs/evals/overview), and [observability](https://mastra.ai/docs/observability/overview).

If you're new to AI agents, check out the [course](https://mastra.ai/course) and [YouTube videos](https://youtube.com/@mastra-ai). You can also join the [Discord](https://discord.gg/BTYqqHKUrf) community to get help and share your projects.
