<!DOCTYPE html>
<html>
<head>
<title>Daily Self-Improvement Links | search.selfnetwork/</title>
<script>
// Define the search queries for each category
const searchQueries = {
  "self-searching": "self-searching techniques",
  "self-knowing": "self-knowing practices",
  "self-enquiry": "self-enquiry exercises",
  "self-awareness": "self-awareness strategies",
  "self-aware-ai": "self-aware AI tools,"
  "presence meditation": "presence meditation,"
  "agni-yoga": "agni-yoga"
};

// Retrieve the top links for a given search query
async function getTopLinks(query) {
  const apiKey = 'AIzaSyAtmn5xLJsokT0i1XvuREPIaAx2JtG8coQ';
  const cx = 'b667ff28003398517';
  const numResults = 21;
  const url = `https://www.googleapis.com/customsearch/v1?key=${apiKey}&cx=${cx}&q=${query}&num=${numResults}&fields=items(link,title)`;

  try {
   const response = await fetch(url);
   const data = await response.json();
   return data.items;
 } catch (error) {
    console.error(error);
 }
}

// Update the HTML with the top links for each category
async function updateLinks() {
  for (const category in searchQueries) {
   const categoryLinks = await getTopLinks(searchQueries[category]);
   const top3Links = categoryLinks.slice(0, 3);
   const categoryList = document.getElementById(`${category}-list`);
   categoryList.innerHTML = ""; // Clear previous links
   for (const link of top3Links) {
   const linkItem = document.createElement("li");
   const linkAnchor = document.createElement("a");
   linkAnchor.href = link.link;
   linkAnchor.textContent = link.title;
   linkItem.appendChild(linkAnchor);
   categoryList.appendChild(linkItem);
    }
  }
}

// Update the links on page load and every 24 hours
window.onload = updateLinks;
setInterval(updateLinks, 24 * 60 * 60 * 1000);</script>
</head>
<body>
<script async src="https://cse.google.com/cse.js?cx=b667ff28003398517"></script>
<div class="gcse-search"></div>
</body>
</html>
In the getTopLinks function, replace the YOUR_API_KEY and YOUR_SEARCH_ENGINE_ID placeholders with your own API key and search engine ID respectively. You can find your search engine ID on the Google Programmable Search control panel.





