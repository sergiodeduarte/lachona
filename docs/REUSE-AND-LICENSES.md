# Reuse, provenance and license inventory

Reviewed 2026-10-30 against the checked-in manifests, installed direct packages and retained notices. This is a source inventory, not a certification of complete license compatibility. Versions below are installed versions, including dependencies inherited from the starter that are not necessarily exercised by the live landing.

## Original work and reused foundations

La Chona's implementation was committed during October 29–30, 2026. Project-specific work includes the Spanish Telegram conversation flow, local model extraction and deterministic validation, durable jobs and request state, verified drinks catalog and matching, access-request and owner-approval workflow, deployment/recovery tooling, landing design/copy iterations and verification. Codex assisted implementation and iteration; it is distinct from the Qwen model used inside the running product.

The project did not create its framework, model or all UI components from scratch:

- The web application began from the supplied Sites/Vinext starter. It retains starter build scripts, framework integration, optional helpers and a shadcn-style UI component library. No separate top-level license file for the starter as a whole was identified in this audit; the plugin notice alone does not establish the license of every starter file.
- The vendored Sites Vite plugin includes an MIT notice, copyright 2026 OpenAI, retained as `landing/scripts/vite/sites-vite-plugin.LICENSE` in the implementation repository.
- The vendored shadcn Tailwind asset includes an MIT notice, copyright 2023 shadcn, retained as `landing/vendor/shadcn-tailwind-4.13.0.LICENSE.md`. Existing UI components are acknowledged as starter reuse, not new La Chona inventions.
- React, Vinext, TypeScript, Cloudflare tooling and the other installed packages below provide the underlying framework and development tooling. Their notices remain with their respective packages.
- The minimal landing took visual-direction inspiration from [Instinct](https://instinct.com/). La Chona uses its own Spanish copy, implementation, colors and glass/citrus artwork; the inspiration is not an affiliation or endorsement.

## Installed direct dependency inventory

“Metadata only” means the installed package declares that license in its `package.json`, but no top-level LICENSE/NOTICE/COPYING file was found in that installed package directory. It does not imply that no license exists upstream. Transitive dependencies and bundled subcomponents may have additional notices; this table is not an exhaustive software bill of materials.

| Package | Installed version | Declared license | Local notice inspected |
| --- | --- | --- | --- |
| @base-ui/react | 1.7.0 | MIT | `LICENSE` |
| @cloudflare/vite-plugin | 1.37.1 | MIT | Metadata only |
| @cloudflare/workers-types | 4.20260515.1 | MIT OR Apache-2.0 | Metadata only |
| @hookform/resolvers | 5.7.1 | MIT | `LICENSE` |
| @shadcn/react | 0.3.0 | MIT | `LICENSE.md` |
| @tailwindcss/postcss | 4.2.1 | MIT | `LICENSE` |
| @types/node | 22.19.19 | MIT | `LICENSE` |
| @types/react | 19.2.14 | MIT | `LICENSE` |
| @types/react-dom | 19.2.3 | MIT | `LICENSE` |
| @vitejs/plugin-react | 6.0.2 | MIT | `LICENSE` |
| @vitejs/plugin-rsc | 0.5.26 | MIT | Metadata only |
| class-variance-authority | 0.7.1 | Apache-2.0 | `LICENSE` |
| clsx | 2.1.1 | MIT | `license` |
| cmdk | 1.1.1 | MIT | `LICENSE.md` |
| date-fns | 4.4.0 | MIT | `LICENSE.md` |
| drizzle-kit | 0.31.10 | MIT | Metadata only |
| drizzle-orm | 0.45.2 | Apache-2.0 | Metadata only |
| embla-carousel-react | 8.6.0 | MIT | Metadata only |
| eslint | 9.39.4 | MIT | `LICENSE` |
| eslint-config-next | 16.3.4 | MIT | Metadata only |
| input-otp | 1.4.2 | MIT | Metadata only |
| json-rpc-2.0 | 1.7.1 | MIT | `LICENSE` |
| lucide-react | 1.31.0 | ISC | `LICENSE` |
| next | 16.3.4 | MIT | `license.md` |
| next-themes | 0.4.6 | MIT | `license.md` |
| radix-ui | 1.6.7 | MIT | `LICENSE` |
| raw-body | 3.0.2 | MIT | `LICENSE` |
| react | 19.2.6 | MIT | `LICENSE` |
| react-day-picker | 10.0.1 | MIT | `LICENSE` |
| react-dom | 19.2.6 | MIT | `LICENSE` |
| react-hook-form | 7.85.0 | MIT | `LICENSE` |
| react-resizable-panels | 4.12.2 | MIT | `LICENSE.md` |
| react-server-dom-webpack | 19.2.6 | MIT | `LICENSE` |
| recharts | 3.8.0 | MIT | `LICENSE` |
| sonner | 2.0.8 | MIT | `LICENSE.md` |
| tailwind-merge | 3.6.0 | MIT | `LICENSE.md` |
| tailwindcss | 4.2.1 | MIT | `LICENSE` |
| tw-animate-css | 1.4.0 | MIT | `LICENSE` |
| typescript | 5.9.3 | Apache-2.0 | `LICENSE.txt` |
| vaul | 1.1.2 | MIT | `LICENSE.md` |
| vinext | 1.0.0-beta.5 | MIT | `LICENSE` |
| vite | 8.0.13 | MIT | `LICENSE.md` |
| wrangler | 4.92.0 | MIT OR Apache-2.0 | Metadata only |
| zod | 3.25.76 | MIT | `LICENSE` |

The root bot has no npm runtime dependencies; its direct development dependencies are `@types/node` and TypeScript. All other entries are from the landing's direct dependency/development manifests. The npm lockfiles record exact resolved versions. The manifest also overrides transitive `sharp` to 0.35.4; that package is outside this direct-dependency table.

The Lucide package declares ISC and its LICENSE also contains the MIT notice for Feather-derived content. Vite's LICENSE includes its own MIT text plus bundled dependency notices. The complete notice files are more informative than their first license heading alone.

## Local inference runtime and model

The application uses Ollama with `qwen3.5:4b`. The installed model manifest references a license layer whose complete local text identifies Apache License 2.0. The inspected license layer digest is `sha256:50cbab8a892c5f2993b8c7351a99182507472def3b1374558308605d99b86b32`. This finding is specific to the installed artifact; it is not a blanket statement about every Qwen model. Model weights are not included in the project repositories.

The locally installed Ollama application contains notices for runtime components including llama.cpp, MLX, XGrammar and other dependencies. A top-level Ollama runtime license was not established from those local notices in this audit. No Ollama binary or bundled runtime libraries are being added to the public showcase. The npm inventory does not cover the complete runtime/model distribution or its notices.

## Supplier data and visual evidence

The priced catalog is based on observations from [La Penca tequila](https://lapencavinos.com/product-category/tequila/), [mezcal](https://lapencavinos.com/product-category/mezcal/) and [whisky](https://lapencavinos.com/product-category/whisky/) category pages, with exact product links and observation timestamps. Its internal evidence archive retains the fetched category HTML and hash receipts for provenance. The public showcase links to sources and explains the observed-data method; raw supplier HTML remains in the private engineering archive. La Chona does not claim ownership of supplier text, trademarks or product imagery. Supplier availability, delivery and changed prices are not guaranteed.

The Codex-use screenshot was supplied by the project owner and authorized for publication as project evidence. It documents a real development session; it does not establish OpenAI endorsement. Landing screenshots document La Chona's own implemented interface. Product logos and third-party UI visible in screenshots retain their respective owners' rights.

## Publication boundaries

No new open-source license is granted to La Chona's original code by this inventory. The implementation repository is private; the public repository is a project showcase with demo instructions, evidence and disclosures. The public README should describe that distinction explicitly. A public GitHub page alone is not an open-source release.

Existing upstream notices are preserved with reused material. Missing starter/runtime license information and transitive dependencies remain outside the verified portion of this audit. The event's eligibility decisions remain with the organizer; this document records known reuse and audit limits rather than asserting eligibility is guaranteed.
