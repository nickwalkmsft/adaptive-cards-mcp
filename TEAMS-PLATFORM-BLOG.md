# Your agent's last mile is the card

*Why the format of an agent's response decides whether it's a teammate or just another chatbot*

---

When a good teammate finishes a task, they don't paste raw output into the channel and walk away. They hand you something you can act on: a short summary, the two numbers that matter, and an **Approve** button right where the conversation is happening. The work moves forward in one place.

Most agents we build don't do that yet. They've gotten remarkably good at *reasoning* - pulling the right data, drafting the right answer. But in a collaborative surface like Microsoft Teams, the response still arrives as a wall of text in a group chat. Everyone reads it, nobody acts on it, and the work stalls in exactly the place it was supposed to accelerate. The intelligence is there. The teammate behavior isn't.

That gap is the last mile of agent quality, and it lives in the response format.

## Text answers; cards move work forward

This is what Adaptive Cards are for. A card turns an agent's answer into something the team can interact with without leaving the conversation: an expense approval with the requester, the amount, and Approve/Reject actions. A deployment notification with a rollback button. An incident alert with acknowledge and escalate. A data table that's actually readable on a phone.

The shift is subtle but it's the whole game. A text response asks a human to *go do something*. A well-built card lets them *do it right there* - and renders natively across Teams, Outlook, and Microsoft 365 Copilot. That's the difference between an agent that talks and an agent that moves work forward.

![Natural language in, a valid, actionable Adaptive Card out](https://raw.githubusercontent.com/VikrantSingh01/adaptive-cards-mcp/main/media/mcp-generate.png)

## High-quality cards are harder than they look

Here's the catch developers hit fast: producing a *good* card is genuinely hard, and it's exactly the kind of work LLMs are bad at.

The Adaptive Cards schema is large. Six host environments enforce different constraints - a card that's perfect in Teams can break in Outlook, which caps the version and the action types. Accessibility properties like `wrap`, `altText`, and `speak` aren't cosmetic; without them the card is unusable for anyone on a screen reader. And the spec moves faster than any model's training data.

Ask a model to free-hand the JSON and it will confidently invent properties that don't exist, drop the accessibility attributes, and emit action types that were deprecated years ago. The card looks plausible and fails to render. Your agent's reasoning was right; its last mile was broken - and that's the part the user sees.

## Give the agent knowledge, not guesses

The fix isn't a bigger prompt. It's giving the agent an authoritative source for the format - a layer that *validates against the real schema*, adapts a card to the host it's headed for, and enforces accessibility, deterministically. Tools don't hallucinate. When the agent checks its work against the actual spec instead of recalling it, the failure modes above simply go away.

If you're building on Teams today, you don't have to assemble that layer yourself. The open-source [adaptive-cards-mcp](https://github.com/VikrantSingh01/adaptive-cards-mcp) server gives any AI assistant - in Copilot Studio, Claude, Cursor, or your own bot - exactly this: generate, validate, optimize, and transform cards for the surface they'll render on. It's one way to close the gap, and it's free to try.

![adaptive-cards-mcp - 9 tools, 3 prompts, 924 tests](https://raw.githubusercontent.com/VikrantSingh01/adaptive-cards-mcp/main/media/hero.png)

## The takeaway

Treat your agent's response format as a first-class design decision, not an afterthought. Ask of every answer: *could a teammate act on this without leaving the chat?* If the answer is no, the agent isn't done - its last mile is.

Building an agent for Teams? Start with the [Teams AI Library and developer docs](https://learn.microsoft.com/microsoftteams/platform/), design your responses as Adaptive Cards from day one, and let your agent verify its own cards instead of guessing. That's how a chatbot becomes a teammate.

**Links:**
- [GitHub](https://github.com/VikrantSingh01/adaptive-cards-mcp)
- [npm](https://www.npmjs.com/package/adaptive-cards-mcp) - `npx adaptive-cards-mcp`
- [MCP Registry](https://registry.modelcontextprotocol.io/?q=adaptive-cards-mcp)
- [Agency Marketplace](https://vigilant-adventure-v9qpqwn.pages.github.io/playground/#plugins/adaptive-cards-mcp)
- [Adaptive Cards Designer](https://adaptivecards.microsoft.com/designer)
- [Watch the demo](https://github.com/user-attachments/assets/372655ce-776c-4e31-a77a-4b2f79f638d2)

---

*Vikrant Singh is a Principal Engineering Manager on Microsoft Teams - Conversational and AI Platform.*

[dummy change to facilitate PR comments]
