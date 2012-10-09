!SLIDE subsection transition=wipe

# What is Tell Don't Ask about?
## "Procedural code gets information then makes decisions. Object-oriented code tells objects to do things"
*Alec Sharp*

!SLIDE bullets incremental transition=zoom

* You should endeavor to tell objects what you want them to do. 
* Do not ask them questions about their state, make a decision, and then tell them what to do.
* Making decisions outside the object violates its encapsulation.
* Design classes based on their responsibilities.
* Data and operations that depend on that data belong in the same object.