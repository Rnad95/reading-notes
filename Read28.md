# Read: 28 - RecyclerView

## Create dynamic lists with RecyclerView

---

### Key classes

Several different classes work together to build your dynamic list.

- RecyclerView is the ViewGroup that contains the views corresponding to your data. It's a view itself, so you add RecyclerView into your layout the way you would add any other UI element.

- Each individual element in the list is defined by a view holder object.

- When the view holder is created, it doesn't have any data associated with it.

- The RecyclerView requests those views, and binds the views to their data, by calling methods in the adapter. The layout manager arranges the individual elements in your list, or you can define your own.

## Steps for implementing your RecyclerView

---

If you're using RecyclerView, you'll need to decide what the list or grid is going to look like. Ordinarily you'll be able to use one of the library's standard layout managers. Based on this design, extend the ViewHolder class to provide all the functionality for your list items. Your view holder is a wrapper around a View, and that view is managed by RecylerView. Define the Adapter that associates your data with the Viewholder views.

## Plan your layout

---
 The RecyclerView library provides three layout managers, which handle the most common layout situations. GridLayoutManager tries to make all the elements in each row have the same width and height, but different rows can have different heights. You'll need this layout when you design the view holder, as described in the next section.

## Implementing your adapter and view holder

---

The ViewHolder is a wrapper around a View that contains the layout for an individual item in a list. The Adapter creates ViewHolds as needed, and sets the data for those views. These two classes work together to define how your data is displayed. When you define your adapter, you need to override three key methods:`onBindViewHolder`, `onInitializeViewHolds` and `onBindViewClients`.

`onCreateViewHolder()`: RecyclerView calls this method whenever it needs to create a new ViewHolder. The method creates and initializes the ViewHolder and its associated View, but does not fill in the view's contents—the ViewHolder has not yet been bound to specific data.

`onBindViewHolder()`: RecyclerView calls this method to associate a ViewHolder with data. The method fetches the appropriate data and uses the data to fill in the view holder's layout. For example, if the RecyclerView displays a list of names, the method might find the appropriate name in the list and fill in the view holder's TextView widget.

`getItemCount()`: RecyclerView calls this method to get the size of the data set. For example, in an address book app, this might be the total number of addresses. RecyclerView uses this to determine when there are no more items that can be displayed.

Here's a typical example of a simple adapter with a nested ViewHolder that displays a list of data. In this case, the RecyclerView displays a simple list of text elements. The adapter is passed an array of strings, containing the text for the ViewHolder elements.

![code 1](https://i.ibb.co/VqLXry1/Screenshot-from-2022-04-28-21-51-52.png)

![code 2](https://i.ibb.co/jWNd9RL/Screenshot-from-2022-04-28-21-52-05.png)