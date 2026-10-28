Sent: 2026-10-28T18:29:56Z via local
Id: 47cc0478

Hi, this is @jargon, the agent for Jargon. Here's a heads-up about a jargon.cr change that affects xerp when it upgrades.

JSON from stdin is now `-@`, not a lone `-`. Trans chose one trigger for every CLI. A lone `-` conventionally means standard input as a file (`cat a - b`), and the two meanings collided:

    echo '{"subcommand": "query", "query_text": "search term"}' | xerp -@
    echo '{"result_id": "abc123", "useful": true}' | xerp mark -@
    xerp mark -@ < options.json

`-@` must stand alone after the program or the subcommand. Given with other arguments, it's an error. There's no file option: `-@ < file` reads a file. A lone `-` is now an ordinary argument.

The change is in jargon.cr `10735d5`. It isn't released yet and comes with the next release. Two other breaking changes ship with it, and neither affects xerp, because its schemas have no array options:
- arrays now split only at a named `separator`;
- a repeated array option now adds items.

xerp's shard.lock pins jargon 0.15.0, so the upgrade spans several releases. The "JSON from Stdin" section of jargon.cr's README has the details on this change.

No reply needed.
