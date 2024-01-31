# Pagination

## Procedure

I created a table element, table head element and I added Id, name and email as their heading with their Id.

I created a empty table body element to display the data

In script file, I stored the data in a variable. 

function loaddata will display the data according to the page number and number of items to be displayed in the current page

First to determine the start index of the current page I subracted - 1 and multiplied by items per page so that it will give the items respective to the page.

To calculate the end page, I added the start index and items per page so it will give us the total number of pages.
```
function loaddata(dataList, itemsPerPage, currentPage) {
  let startIndex = (currentPage - 1) * itemsPerPage;
  let endIndex = startIndex + itemsPerPage;
```

To get the data from the object I took 3 empty array as a variable.

Using the for loop with start Index as the input for the i and not more than the number of pages and total number of objects I pushed the index value to the empty string.
```
 for (let i = startIndex; i < endIndex && i < dataList.length; i++) {
    dataId.push(dataList[i].id);
    dataName.push(dataList[i].name);
    dataEmail.push(dataList[i].email);
  }
```
As I have said earlier i created a empty table body element, now it has been stored in a variable using **getElementById** and I created the empty html string

Using the for loop and keeping the number of Id as limit I created the row and table element and appended the data in between the tags

for every loop it will append the data to the tablebody element.

```
  let dataId = [];
  let dataName = [];
  let dataEmail = [];

for (let i = 0; i < dataId.length; i++) {
    html += "<tr>";
    html += "<td class='col-xxl-1 col-md-1 col-1'>" + dataId[i] + "</td>";
    html += "<td class='col-xxl-3 col-md-2 col-3'>" + dataName[i] + "</td>";
    html += "<td class='col-xxl-4 col-md-2 col-4' >" + dataEmail[i] + "</td>";
    html += "</tr>";
  }

  tableBody.innerHTML = html;
}
```
To create the pagination I wrote a function that takes data objects and items per page as input.

Then I calculated the total pages by dividing the total number of objects by items per page and i rounded of to the nearest number using **Math.ceil** 

Using for loop i created the button element the index value as inner text.

```
function createPagination(dataList, itemsPerPage) {
  let totalPages = Math.ceil(dataList.length / itemsPerPage);
  let paginationDiv = document.getElementById("pagination");
  let html = "";

  for (let i = 1; i <= totalPages; i++) {
    html += `<button class="p-1 m-1 text-primary " style="width:2em; height: 1 em; " onclick="changePage(${i})">${i}</button>`;

  }

  paginationDiv.innerHTML = html;
}

```







