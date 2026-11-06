# edw-orchestration-2 · Writers' Room

A six-agent cooperative orchestration demo. Six LLM writers sit around a round
table with a flower pot blocking across-the-table whispers. Each round:

1. Every writer whispers to its two neighbors and votes for an ordered pair
   `A → B` to collaborate.
2. The pair with the plurality composes a transformation: `A` applies its skill
   to the shared artifact, then `B` takes `A`'s output and applies its own skill.

Starting from a one-word seed, the group iterates for three rounds. Each writer
has exactly one discrete skill:

| Seat | Shape    | Skill         | What it does                                |
| ---- | -------- | ------------- | ------------------------------------------- |
| 0    | Triangle | Imagist       | adds one concrete sensory image             |
| 1    | Square   | Metaphorist   | introduces one metaphor                     |
| 2    | Pentagon | Juxtaposer    | places two unlike elements in contrast      |
| 3    | Hexagon  | Rhythm-keeper | reorders words for cadence; no new material |
| 4    | Heptagon | Compressor    | cuts roughly a third of length              |
| 5    | Octagon  | Polisher      | light sound / grammar edit                  |

## Running locally

```bash
npm install
cp .env.local.example .env.local  # then paste your Anthropic key
npm run dev
```

All agent decisions use Claude Haiku 4.5 via the Vercel AI SDK. A full run is
24 LLM calls (6 votes × 3 rounds + 2 transformations × 3 rounds) and takes
~30–45 s.
