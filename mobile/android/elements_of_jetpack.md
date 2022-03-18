# Elements of Android Jetpack

[*link*](https://commonsware.com/Jetpack/pages/index)

## Employing `RecyclerView`

- Two major types of `ViewGroup`s:
  - Compile time
    - Constraintlayout, Linear Layout
  - Run time
    - RecyclerView & AdapterView family of classes (ex: ListView)

- RecyclerView and Adapterview are designed around recycling
  - Ex: display only set # of items at a time, and offload the items that are out of user view

- RecylcerView
  - Mainly responsible for view recycling
  - Other classes to be used with recylcerview:
    - layout manager to organize the views into structures (vertical list, grid, staggered grid, etc)
    - item decorator to apply effects and light positioning to views (ex: divider line)
    - item animator to apply animated effects (ex: model data changes)

- `View` can be used to render color since it doesn't render anything else like text, image, etc

- Making a row interactable
  - android:background="?android:attr/selectableItemBackground"
    - makes ripple effect
    - otherwise constraintlayout background is transparent    
  - android:clickable="true"
  - android:focusable="true"

- Viewholder (see p 270)
- toast 
  - transient message that displays and dissappears on its own without user interaction
  - good for advisory messages where if user misses them, then no problem
  
- Adapter (see p 272)
