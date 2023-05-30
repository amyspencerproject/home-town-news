# Home Town News

## Website using all the concepts I learned about CSS Grid

## Notes/Definitions
**fractional unit:** measurement of the amount of free space available for a row or column to stretch. Fractional units, `1fr` divvy up the extra space in a grid container *without* declaring a specific width or height. Similar to the `flex-grow` property, the fractional unit tells an item how much extra space to take up.

**flex-basis:** a property that sets the initial size of a flex item. Flex-basis can be set as a number, percentage, or other value. Let’s say you have three flex items. You want to set each item to 200px wide. You can use flex-basis to set the size of each by writing:

```
flex-basis: 200px;
```

**flex-grow:** a property that assigns extra space to a specific flex item within a flex container. The extra space is determined by the size of the flex container minus the amount of space the flex items take up. For instance, if your flex container is 1000px wide, and your three flex items total 600px wide, then you’ll have 400px of extra space. You can use any positive number to indicate how much extra space to assign, like “flex-grow: 1;”. The higher the value you assign to flex-grow, the more extra space the flex item will take up. By default, flex-grow is set to 0.

**flex-shrink:** dictates how flex items will shrink when they don’t fit inside the flex container. By default, flex-shrink is set to 1, so all elements will shrink to fit the parent container. When you set flex-shrink higher than 1 for a flex item, it will shrink to take up half as much space as the other flex items.

********flex********: shorthand property which uses flex-grow, flex-shrink, *and* flex-basis at the same time. Like this `flex: 2 1 200px`

**Three** main ways to **align** in CSS Grid

1. Align items in the **Grid Container** with **justify-items** (horizontally) and **align-items** (vertically)
2. Align the item itself with an ************align-self************  or ************justify-self************ property
3. Align by selector, ****************************first-of-type****************************, ************************last-of-type************************, and **********************nth-of-type**********************
You can get very specific with selections with `(n + number)`
    
    ```jsx
    .topic:first-of-type {
      align-self: end;
    }
    
    .topic:last-of-type {
      align-self: end;
    }
    
    .topic:nth-of-type(3) {
      align-self: end;
    }
    .topic:nth-of-type(n + 4) {
      align-self: end;
    }
    ```
    

**repeat() function:** creates duplicate rows and columns based on values for the number and size of the rows or columns. The `repeat()` functions get added to the `grid-template-columns` and `grid-template-rows` properties when you want to create multiple rows or columns of an equal width.  [MDN Link](https://developer.mozilla.org/en-US/docs/Web/CSS/repeat)

**grid-template:** [MDN Link](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows)

**grid-column** and **grid-row:** combines the column and row start and end properties into a single property. For example, `grid-column-start` and `grid-column-end` become one `grid-column` property with the starting and ending grid line for the column separated by a forward slash.

```jsx
**grid-column: 2 / 4;
grid-row: 1 / 6;**
```

**span keyword:** tells a row or a column to take up a specific number of rows or columns without defining the specific grid line the row or column will end at. The example below will have columns start at grid line 1 and will span four columns.

```jsx
**grid-column: 1 / span 4;**
```

**grid-column-gap** and **grid-row-gap property** allows you to add a gap, or space, between  columns and rows. Values can be pixels or percentages. The **grid-gap property** combines grid-gap-column and grid-gap-row into the same property.

```jsx
grid-column-gap: 10px;
grid-row-gap: 5%;
grid-gap: 30px;
```

**Negative Numbers:** a negative number added to the value of `grid-column` and `grid-row` properties will count backward from the last grid line. For instance, if you add a `-1` at the end of the `grid-column` value, the column will end at the last grid line, no matter how many grid lines are present.

```jsx
**grid-column: 1 / -1;**
```

**explicit grid:** defined number of rows and columns, used for *precisely* controlling the exact layout.

**implicit grid:** automatically arranges columns and rows based on element size, free space, and screen size. Elements will stay the perfect size and can automatically fill up any extra rows and columns. Do not need to rely on media queries.

**minmax():** defines the minimum and maximum values of grid items, which is handy when you want to define the smallest and largest value for a specific column or row so elements will never be undersized or oversized in your layout. In the example below the info section will contain a row that is 200 pixels wide, a second row that is 300 pixels wide, and a third row with a minimum width of 150 pixels and a maximum width of 1 fractional unit.

```jsx

.info__section {
	grid-template-rows: 200px 300px minmax(150px, 1fr);
}
```

**auto-fill keyword:** automatically wraps as many items on a grid track as possible without resizing the elements, which is helpful when you want your rows filled with columns, but you don’t want your elements to be stretched.

```jsx
.grid__container__one {
	grid-template-columns: repeat(auto-fill, minmax(75px, 1fr));
}
```

**auto-fit keyword:** fills the grid track with as many items as possible and expands the elements to fit the page. Any empty columns are collapsed so the items take up the full width. Like the `auto-fill` keyword, you’ll add the `auto-fit` keyword in the `repeat()` function.

```jsx
.grid__container__two {
	grid-template-columns: repeat(auto-fit, minmax(75px, 1fr));
}
```

**nth-child selector:** select and style an element based on their relationship to a parent element and their position among sibling elements. 

```jsx
.elements:nth-child(3) {
	text-align: right;
}

.elements:nth-child(3n) {
  text-align: right;
}
```

**Grid-auto-flow:** controls the way grid items are automatically placed in the grid track.

**Grid-auto-rows:** specifies the height of the rows *not* explicitly defined (AKA your implicit grid)
