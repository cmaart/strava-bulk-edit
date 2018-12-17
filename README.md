strava-bulk-edit
========================

_2018-12-07 Update: This no longer works with the latest updates to the Strava site._


## Workaround for now

Paste this in your Console in the developer tools (F12) and change 'everyone' near the bottom to the visibility you want to have for all activities. Possible values are: 'everyone', 'followers_only' and 'only_me'

```js
(function() {

this.changeVisibility = (visibility) => {
		document.querySelectorAll('select[name="visibility"]').forEach(selectEl => {
			selectEl.value = visibility;
        });
		setTimeout(() => {
		document.querySelectorAll('td.edit-actions button[type="submit"]').forEach(saveBtnEl => {
			saveBtnEl.click();
        })}, 1000);
		setTimeout(done, 5000);
}

var done = () => {
	var nextButton = document.querySelector('button.next_page:not(.disabled)');
	if(nextButton) {
		nextButton.click();
		setTimeout(this.changeVisibility, 2000);
    }
	console.log('done')
};

this.changeVisibility('everyone');

})();


```

## Disclaimer

This is in not affiliated with Strava, Inc. in any way. The term STRAVA and the Strava logo are the exclusive trademarks of, and are owned by, Strava Inc.

## LICENSE

MIT
