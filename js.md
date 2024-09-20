# Bookmarks_to_Clipboard

After exporting booksmarks to HTML, this Javascript copies the links to your clipboard. Save the Javascript as a bookmark for ease of use.

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


