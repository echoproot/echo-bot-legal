# Privacy Policy — Echo

**Last updated:** 2026.07.22

This policy explains what data the Echo Discord bot ("the Bot") collects, why it collects it, and what your rights are. It applies to everyone who interacts with the Bot.

**Data controller:** Solymosi Bendegúz, Hungary — contact: echoprootshop@gmail.com 

## 1. What we store

Echo stores as little as possible. The only data written to persistent storage is:

| Data | When it is stored | Why |
|---|---|---|
| Discord server (guild) ID | When an administrator runs `/setup_echo`, `/setup_music` or `/setup_ai` | To know which server a setting belongs to |
| Discord channel ID | Same as above | To know where to send scheduled messages, now-playing embeds or AI replies |

These are numeric identifiers assigned by Discord; they contain no names, email addresses or message content. If nobody runs a setup command, nothing is written to storage at all.

## 2. What is processed temporarily but not stored

- **Command inputs** — parameters you pass to a command (a search term for `/play`, a mentioned user for `/hug`) are handled in memory to build a response and are not written to a database.
- **Public profile data** — `/avatar` and mention-based commands read publicly available Discord profile information at the moment the command runs. Nothing is retained afterwards.
- **Voice audio** — the Bot transmits audio into voice channels. It does not record, listen to or store voice.
- **AI conversation context** — a short buffer of recent messages, held in the Bot's working memory only. See section 4.

## 3. Message content

The Bot uses Discord's **Message Content privileged intent**. We want to be transparent about what that means in practice.

**Why it is needed.** Two optional features rely on reading ordinary messages rather than slash commands:

- **Music channel** (`/setup_music`) — in the designated channel you can request a track by typing `play <song>` without a slash. The Bot deletes your message straight away and updates a single "Now Playing" panel instead, so the channel stays tidy.
- **AI channel** (`/setup_ai`) — in the designated channel you can talk to the Bot normally, without prefixing every message.

**What this means technically.** Because Discord grants this intent at the application level rather than per channel, the Bot's connection technically receives message content from channels it can see. The Bot only *acts on* messages in the two channel types listed above. Everything else is discarded immediately in code: it is not stored, not logged, not sent to any third party, and not read by a human.

**In the music channel**, the text of a `play` request is used to search for the track and is then discarded along with the deleted message. Slash command replies in that channel are either shown only to you or removed automatically after a few seconds.

**Direct messages** to the Bot are not processed.

If you would rather the Bot never receive content from a given channel, deny it the "View Channel" permission there.

## 4. AI conversation channel (optional)

If a server administrator enables the AI channel using `/setup_ai`, messages posted **in that channel only** are forwarded to **Groq, Inc.** (GroqCloud API) so that a reply can be generated. No other channel's content is transmitted anywhere.

**Conversation history.** To keep replies coherent, the Bot holds a short rolling conversation buffer for each user, keyed by Discord user ID. Only the **six most recent messages** (roughly three exchanges) are kept; each new message pushes the oldest one out. This buffer exists **in the Bot's working memory only — it is never written to disk, and it is erased entirely whenever the Bot restarts.** It is never shared with anyone other than the AI provider named above.

**Groq as sub-processor.** According to Groq's published documentation, customer data is not retained by default for inference requests; inputs and outputs may be logged temporarily only to troubleshoot platform errors or investigate suspected abuse, and such logs are kept for up to 30 days. Groq does not use API inputs or outputs to train or fine-tune models. See [Groq's privacy policy](https://groq.com/privacy-policy) and [Your Data in GroqCloud](https://console.groq.com/docs/your-data).

**International transfer.** Groq is based in the United States and stores any retained data there. Enabling this feature therefore means message content from that channel is transferred outside the EEA. Where applicable, Groq relies on standard contractual clauses for such transfers.

**Please do not share personal or sensitive information in the AI channel.**

## 5. Technical logs and developer tools

Basic operational logs (errors, command names, timestamps and guild IDs) may be written for debugging purposes. They are not used for profiling or analytics and are kept for no longer than [30] days.

The `/debug_mem` command is restricted to the Bot's developer and displays the Bot's current runtime state (such as the list of configured servers and channels). It is not available to server administrators or ordinary users, and it does not expose message content.

## 6. What we never collect

- Stored copies of message content — nothing beyond the six-message in-memory buffer described in section 4
- Direct messages
- Email addresses, IP addresses, passwords or payment information
- Voice recordings
- Any special category personal data

Data handled by the Bot is never sold, rented or shared with advertisers.

## 7. Legal basis (GDPR)

Where the GDPR applies, processing is based on our legitimate interest (Art. 6(1)(f) GDPR) in operating the features of a bot that has been voluntarily added to your server, and — for the optional AI and music channels — on the explicit action of the server administrator who enabled them.

## 8. Retention and deletion

Stored guild and channel IDs are kept only while they are needed. To have them deleted:

- **Remove the Bot from your server** — the associated configuration is deleted automatically; or
- **Email us** at echoprootshop@gmail.com with your server ID, and all stored data will be deleted within 30 days.

Your AI conversation buffer clears itself: it holds at most six messages, and it is erased completely every time the Bot restarts. No action is needed to delete it.

## 9. Your rights

Under the GDPR you have the right to access, rectify, erase, restrict or object to the processing of your data, and the right to data portability. Given how little the Bot stores, most requests are satisfied simply by deletion. Contact echoprootshop@gmail.com to exercise these rights.

You also have the right to lodge a complaint with your national supervisory authority. In Hungary this is the Hungarian National Authority for Data Protection and Freedom of Information (NAIH).

## 10. Children

The Bot is not directed at children below Discord's minimum age requirement (13, or higher where local law requires). We do not knowingly collect data from them. If you believe we have, contact us and it will be deleted.

## 11. Changes

This policy may be updated. The current version is always available at this URL, and the "Last updated" date reflects the most recent change.

## 12. Contact

echoprootshop@gmail.com · discord: echo.the.proot
