# Bridge Solver Online

A slightly modified version of John Goacher's [Bridge Solver Online](https://mirgo2.co.uk/bridgesolver/index.php) (BSOL). Based on version 1.0.8

## Change
The only change is that when another board is selected, this is posted as a message in javascript so that the parent process also knows this. The only file that is changed is `ddummy6.js`.

```javascript
//  2025-06-28 START
	if (window.parent) {
		try {
			var boardNumber = g_hands.boards[g_lastBindex].board;
			window.parent.postMessage(JSON.stringify({ type: 'boardChange', boardNumber: boardNumber }), '*');
		} catch (e) {
			// ignore error
		}
	}
//	2025-06-28 END
```

## How to use
Run `npm run serve`. The Bridge Solver is available on http://localhost:3002/bsol/ddummy.htm. See `package.json` for the port setting.

Example usage: http://localhost:3002/bsol/ddummy.htm?file=/tournaments/test.pbn. This will show the tournament stored in `/public/tournaments/test.pbn`.