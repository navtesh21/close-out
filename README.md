# Close-out

My submission for the RideOps Support case study (Navtesh Maken, 2023UIC3641).

Close-out is a check an L1 agent goes through before closing a ticket. It shows how often that kind of ticket has been reopened, lists what to confirm first, and drafts a reply telling the client what to look out for. It opens as Karan B, who has the highest reopen rate in the export. You can switch agents from the sidebar.

Live version: https://navtesh21.github.io/close-out/

## Running it locally

You need `index.html` and `tickets.csv` in the same folder. From that folder:

```
python3 -m http.server 8000
```

Then open http://localhost:8000.

You can also just double-click `index.html`. Some browsers won't let a page read a file sitting next to it. If you get the "Load the ticket export" screen, click "Choose tickets.csv" in the sidebar and select the file.

Nothing needs installing. It all runs in the browser and no data leaves your machine.

## Using it

My tickets is a board with three columns. Ready to close has the agent's tickets that are with L1 right now, tagged high, medium or low reopen risk. Follow up has medium and high risk tickets closed in the last 3 days, plus anything closed without confirmation. Closed here shows what was closed through the tool today.

Click a ticket in Ready to close to start closing it. It takes four steps: why it might come back, the checks for that problem, how you know it's fixed (client confirmed, checked it myself, or not yet), and a draft reply to the client. High risk tickets, and anything closed without confirmation, get a follow-up 2 days later. Mark a follow-up checked once you've messaged the client.

My record compares the agent's reopen rate with the rest of the team, by week and by problem type, and lists the tickets that came back.

To try the steps on an old ticket, type its ID (for example SUP-11319) in the box above the board.

## How the risk tag works

I group tickets by their description with the numbers stripped out, so "duplicate entries for 7 employees" and "duplicate entries for 12 employees" count as the same symptom. The tag is that symptom's reopen rate, pulled toward the overall rate so a symptom with only a few tickets doesn't jump around. 14% or more is high and 9 to 14% is medium. A ticket that's already been reopened is always high.

The checklists are in `PLAYBOOK` near the top of the script in `index.html`. There are 16 of them and between them they cover all 48 symptoms in the export. A team lead can edit them there.

The app takes the last timestamp in the export as "now". A newer export can be loaded from the sidebar as long as it has the same columns.

## Limits

Closing a ticket here doesn't close it in the helpdesk. Closes and follow-ups are saved in the browser only. I wrote the checklists from the symptom descriptions, so they should be checked with the team lead before anyone relies on them.
