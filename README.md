# Vendetta Scripts — Free Roblox Scripts

Three free Roblox scripts, released with full, readable source. No dependencies, no account needed — download them, read them, use them in whatever you're building.

The rest of the catalogue — larger Roblox systems and FiveM QBCore resources — lives at **[venscripts.dev](https://venscripts.dev)**.

💬 **Join the Discord** for help, updates and new free scripts: [discord.gg/9VaUnWTahk](https://discord.gg/9VaUnWTahk)

---

## What's in here

| Script | What it does | Where it goes |
| --- | --- | --- |
| [Admin Kick Command](#admin-kick-command) | Chat command letting listed admins kick players | `ServerScriptService` |
| [Killbrick](#killbrick) | Any part becomes lethal on touch | Inside the brick |
| [Shop to Base Teleport](#shop-to-base-teleport) | Teleport pad that sends players to a fixed point | Inside the pad |

All three run **server-side**, so none of them can be bypassed or triggered by a client.

---

## Admin Kick Command

Lets the people you list kick players straight from the chat.

**Placement:** `ServerScriptService`, as a **Script** (not a LocalScript).

**Setup:** add your admins' User IDs to the config block at the top.

```lua
local ADMIN_IDS = {
    1234567,
}
```

> Find a User ID in the profile URL: `roblox.com/users/`**`1234567`**`/profile`.
> Remember to delete the `--` in front of the line, or the entry is only a comment.

**Usage:** `/kick PlayerName`

Partial names work, so `/kick ste` will find `Steve123`. The game owner always has access on user-owned places, even with an empty list.

**Notes**
- `PROTECT_ADMINS` stops admins kicking one another. On by default.
- `ALLOW_SELF_KICK` lets you kick yourself, which is handy for testing.
- The command is read from `Player.Chatted` on the server, so the admin check can't be faked by an exploiter.
- Results are printed to the **server console**, not in-game chat.

---

## Killbrick

Turns any part into an instant kill on contact.

**Placement:** inside the brick, as a **Script** (not a LocalScript).

**Setup:** none. Drop it in and the brick is lethal.

**Notes**
- Kills anything with a `Humanoid`, NPCs included.
- Works through spawn ForceFields, since it sets health directly.

---

## Shop to Base Teleport

A pad that moves players to a fixed destination — a shop exit back to a home base, for example.

**Placement:** inside the teleport pad Part, as a **Script** (not a LocalScript).

**Setup:** create the destination and name it to match the config.

```lua
local DESTINATION_NAME = "DestinationHomeBase1"
local HEIGHT_OFFSET = 3   -- studs above the destination
local COOLDOWN = 1        -- seconds before the same player can re-trigger
```

The destination can be a **Part or a Model**, and it can sit anywhere in `Workspace` — including inside a folder.

**Notes**
- The cooldown is **per player**, so one person using the pad never blocks anyone else.
- Uses `PivotTo` to move the whole character, which avoids the rubber-banding you get from setting `HumanoidRootPart.CFrame` directly.
- If the destination is missing or misnamed, the pad says so in the Output window rather than failing silently.

---

## Installing

1. Open your place in Roblox Studio.
2. Create a **Script** in the location listed above for the one you want.
3. Paste the contents of the file over the default `print("Hello world!")`.
4. Edit the configuration block at the top if the script has one.
5. Press **Play** and check the **Output** window.

Every script reports setup problems in Output with a `[ScriptName]` prefix. If something isn't working, that's the first place to look — a missing team, an empty admin list or a misspelled destination will name itself there rather than failing quietly.

---

## License

Released under the [MIT License](LICENSE). Use them in personal or commercial projects, modify them freely — just keep the copyright notice.

---

## Support

Issues and pull requests are welcome on this repo, or ask in the [Discord](https://discord.gg/9VaUnWTahk).

For the paid scripts, support comes directly from me — see [venscripts.dev](https://venscripts.dev).
