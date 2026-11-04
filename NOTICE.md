# Notice & Credits

SmartRecipe is released under the [MIT License](LICENSE). It stands on the work of others, credited below.

## Upstream project

SmartRecipe is a fork of **[smart-recipe](https://github.com/gerkensm/smart-recipe)** by **Torben Gerkensmeyer**
([@gerkensm](https://github.com/gerkensm)), which provided the original architecture: the recipe pipeline, the dual-schema
design, the Monsieur Cuisine Smart and Cookidoo clients and the CLI. His copyright notice is preserved in
[`LICENSE`](LICENSE). This fork adds the Claude Desktop extension (MCP server and recipe cards) and further
device and workflow changes.

## Community projects that inspired the Thermomix (Cookidoo) integration

- [@recode-software/cookidoo-api](https://github.com/recode-software/cookidoo-api) (TypeScript) by Recode Software.
- [cookidoo-api](https://github.com/miaucl/cookidoo-api) (Python) by Cyrill Raccaud (`miaucl`).

They were invaluable references for Cookidoo API routes, authentication flows and schema structures.

## Third-party software

| Package | License | Author | Used for |
| --- | --- | --- | --- |
| [Playwright](https://playwright.dev) (`playwright`, `playwright-core`) | Apache-2.0 | Microsoft Corporation | Browser sign-in to Cookidoo and Monsieur Cuisine. Bundled in the Claude extension with its own `LICENSE` and `NOTICE`. |
| [openai](https://github.com/openai/openai-node) | Apache-2.0 | OpenAI | LLM recipe generation |
| [better-ajv-errors](https://github.com/atlassian/better-ajv-errors) | Apache-2.0 | Rifat Nabi | Readable schema validation errors |
| [Model Context Protocol ext-apps](https://github.com/modelcontextprotocol/ext-apps) and [mcpb](https://github.com/anthropics/mcpb) | MIT | Anthropic | Claude Desktop extension: recipe cards and packaging |
| [TypeBox](https://github.com/sinclairzx81/typebox) | MIT | sinclairzx81 | Schemas |
| [Ajv](https://ajv.js.org) | MIT | Evgeny Poberezkin | JSON Schema validation |
| [Cheerio](https://cheerio.js.org) | MIT | Matt Mueller and contributors | HTML parsing |
| [Defuddle](https://github.com/kepano/defuddle) | MIT | kepano | Extracting the recipe from web pages |
| [linkedom](https://github.com/WebReflection/linkedom) | ISC | Andrea Giammarchi | Server-side DOM |
| [marked](https://marked.js.org) and [marked-terminal](https://github.com/mikaelbr/marked-terminal) | MIT | Christopher Jeffrey, Mikael Brevik | Markdown and terminal rendering |
| [Commander](https://github.com/tj/commander.js) | MIT | TJ Holowaychuk | CLI |
| [Inquirer.js](https://github.com/SBoudrias/Inquirer.js) | MIT | Simon Boudrias | Interactive prompts |
| [ora](https://github.com/sindresorhus/ora) | MIT | Sindre Sorhus | Spinners |
| [pino](https://getpino.io) and [pino-pretty](https://github.com/pinojs/pino-pretty) | MIT | Matteo Collina, James Sumners | Logging |
| [tsup](https://tsup.egoist.dev), [Vitest](https://vitest.dev), [TypeScript](https://www.typescriptlang.org) | MIT / Apache-2.0 | EGOIST, Anthony Fu, Microsoft | Build, test and types (development) |

Each package keeps its own license, shipped inside its `node_modules` folder. Transitive dependencies are covered by
their own licenses too.

## Trademarks

Monsieur Cuisine, Lidl, Silvercrest, Thermomix, Vorwerk, Cookidoo, OpenAI, Claude and Anthropic are trademarks of their
respective owners. SmartRecipe is independent and not affiliated with or endorsed by any of them.
