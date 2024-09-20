# Bookmark Extractor to Clipboard

This simple JavaScript snippet allows you to extract all the links and titles from an HTML bookmark export and copy them directly to your clipboard. It is particularly useful if you want to quickly grab and organize your bookmarks.

## How It Works

1. **Selects Bookmark Elements**: The script scans the document for `<a>` elements (links) within `<dt>` tags and for `<h3>` elements (folder titles) within the bookmark HTML structure. 
2. **Formats the Output**: Links are formatted with their text content and URL, while folder titles are formatted as headers with a `#` symbol.
3. **Copies to Clipboard**: The output is copied to the clipboard using a hidden `textarea` element to facilitate the copy operation.
4. **User Notification**: The script alerts the user once the bookmarks have been successfully copied.

### Code Breakdown

```javascript
javascript:(function(){
  var result = [].map.call(document.querySelectorAll("dt a, h3"), function(a) {
    return ((a.href) ? "" : "\n# ") + a.textContent + ((a.href) ? " - " + a.href : " #");
  }).join("\n");

  var textarea = document.createElement("textarea");
  textarea.value = result;
  document.body.appendChild(textarea);
  textarea.select();
  document.execCommand("copy");
  document.body.removeChild(textarea);

  alert("Bookmarks copied to clipboard!");
})();


