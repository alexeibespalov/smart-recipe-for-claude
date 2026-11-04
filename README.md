# Smart Cooker for Claude

**Tell Claude to put a recipe on your Monsieur Cuisine Smart or Thermomix.**

Smart Cooker is a [Claude Desktop](https://claude.com/download) extension. Share a recipe link or paste a recipe and
Claude rewrites it as a guided machine recipe, with weighing, chopping, sautéing, kneading and steaming steps and real
times, temperatures and speeds, in your language. It then sends the recipe to your cooker account.

> *"Put this on my cooker: https://example.com/my-favorite-recipe"*

Claude writes the recipe itself, so **no OpenAI or other AI API key is needed**. The extension fetches the source,
checks Claude's recipe against the physical limits of your device, and uploads it. It never decides what to cook.

> [!IMPORTANT]
> Supports the **Monsieur Cuisine Smart / MC3.0** (Lidl; not the older connect / MC2.0) and the **Thermomix TM7, TM6
> and TM5** through Cookidoo.

---

## How it works

1. **Share a recipe.** Paste a link from any website, a Cookidoo or Monsieur Cuisine link, or the recipe text.
2. **Claude writes the cooker recipe.** The extension gives Claude the device rules, the exact schema and the source
   text. Claude produces the structured recipe.
3. **The recipe is checked.** Speed limits while heating, jug capacity, accessory modes you do not own and other device
   limits are validated. Claude fixes any error before you see the result.
4. **You confirm.** Claude shows the recipe as a card in the chat and asks *"Send it?"*.
5. **It lands on your cooker.** Monsieur Cuisine recipes are published to your **private** library so they show up on
   the cooker touchscreen. Thermomix recipes go to Cookidoo Created Recipes.

Recipes are never submitted to the community. A web-only draft is created only if you ask for one.

### Recipe cards

Sending a recipe, or asking *"What's on my cooker?"*, shows colourful cards inline in the chat: photo, servings and
timings, nutrients, an ingredient table (⚖️ marks what the scale weighs) and every step colour-coded by what the machine
does, with mode badges and time, temperature and speed chips. Light and dark themes follow Claude Desktop.

---

## Install

1. Download the newest [`claude/releases/smart-cooker-<version>.mcpb`](claude/releases/).
2. Double-click it, or drag it into **Claude Desktop → Settings → Extensions**, and click **Install**. When updating,
   remove the old Smart Cooker extension first.
3. In the extension's settings choose:
   - **Default cooker**: Monsieur Cuisine Smart or Thermomix
   - **Recipe language**: en-US, de-DE, fr-FR, it-IT, pl-PL or cs-CZ (you can still ask Claude for another language per
     recipe)
   - **Food-processor attachment** (Monsieur Cuisine): allow the slicing and grating mode only if you own it
   - **Thermomix model**: TM7, TM6 or TM5

Claude Desktop runs the extension on its built-in Node, so there is nothing else to install.

### Connect your account

Ask Claude: *"Connect my Monsieur Cuisine account"* (or Cookidoo). The official login page opens in a browser window.
Log in once. The session is saved on your computer in `~/.smart-recipe` and is never shown in the conversation. The
first login can take a minute while a login browser downloads. If that browser cannot be used, set
`SMART_RECIPE_BROWSER_CHANNEL=chrome` to use your installed Chrome instead.

---

## What you can ask

| Ask Claude… | What happens |
| --- | --- |
| "Put this on my cooker: *link*" | Fetches, writes, validates and (after you confirm) uploads the recipe |
| "Make it for Thermomix, in German" | Overrides the default cooker or language for one recipe |
| "What's on my cooker?" | Shows a grid of your recipes with thumbnails and 📱 On cooker / 📝 Draft badges |
| "Is my login still working?" | Checks the session and shows the active settings |
| "Save it as a draft only" | Creates a web-only draft instead of publishing it privately |

### Tools

The extension exposes these tools to Claude. The conversation workflow (when to use them, confirm before sending, how
to present recipes) travels in the tool descriptions, so no separate skill is needed.

| Tool | Purpose |
| --- | --- |
| `prepare_recipe` | Fetch a recipe and return the device rules, schema and source text |
| `validate_recipe` | Check Claude's recipe against the device schema and physical limits |
| `upload_recipe` | Send a validated recipe to the cooker account |
| `list_recipes` | List recipes and drafts on the account |
| `check_connection` | Check the session and the active settings |
| `connect_account` | Open the official login window |
| `job_status` | Get the result of a long-running step |

The same MCP server is available as `smart-recipe-mcp` for other MCP clients.

---

## Safety and privacy

* **Hardware limits are enforced.** Rules come from the official operating manuals: speed 1 to 10, speeds 7 to 10 for at
  most 10 minutes, Roast at most 500 g, steamer water, kneading cooldown, accessory names and reference times and
  temperatures. Recipes that break them are refused.
* **You confirm every upload.** Nothing is sent without your say-so.
* **Your login stays local.** Cookies are stored on your computer and are not shown to Claude.
* **Check before cooking.** Claude can be wrong. Review quantities, allergens, food safety, times and temperatures.
* Recipe websites and images may be protected by copyright. Make sure you may use what you import.

SmartRecipe is an independent open-source project. It is not affiliated with or endorsed by Lidl, Monsieur Cuisine,
Silvercrest, Vorwerk, Thermomix, Cookidoo or Anthropic.

---

## Also available as a CLI and library

The same engine ships as a command line tool (`smart-recipe`) and a TypeScript library. The CLI can also generate
recipes with its own OpenAI key. See [docs/cli.md](docs/cli.md) for commands, login options, locales and
troubleshooting, [docs/api.md](docs/api.md) for the library API and [docs/technical.md](docs/technical.md) for
implementation notes.

## Build the extension

```bash
npm install
npm run build:claude -- --bump patch   # writes claude/releases/smart-cooker-<version>.mcpb
```

Without `--bump` the build refuses to overwrite an existing release (`--force` rebuilds it). Add a line to
[`claude/CHANGELOG.md`](claude/CHANGELOG.md) for each release. More in [claude/README.md](claude/README.md). Before
architectural changes read [`AGENTS.md`](AGENTS.md).

```bash
npm run typecheck
npm test
```

---

## Credits

This project is a fork of [gerkensm/smart-recipe](https://github.com/gerkensm/smart-recipe) by Torben Gerkensmeyer, and
builds on [Playwright](https://playwright.dev) and other open-source software. The Cookidoo integration was inspired by
[@recode-software/cookidoo-api](https://github.com/recode-software/cookidoo-api) and
[cookidoo-api](https://github.com/miaucl/cookidoo-api). Full credits are in [NOTICE.md](NOTICE.md).

## License

MIT. See [LICENSE](LICENSE).
