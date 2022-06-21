# Computer Vision Challenge

This challenge offers a good insight into one of the core problems we solve at Waldo: how to
match together the visual representation of a screen and its view hierarchy.

## Submit

You should have received an upload link from us. Please zip your work once it's complete and upload it there.

## Input

In `/samples`, you will find a list of pairs `${name}.json` and `${name}.jpg`. They are the 2
representations for the same screen `${name}`.

The view hierarchy file follows a fairly straightforward structure. The important thing to note is
that nodes are flattened, but in fact they represent a tree structure. You can easily get the tree
structure by looking at parentIndex and index.

## Goals

The goal is to answer this philosophical question: "if I look at coordinates x, y, what box is
actually responsible for the pixel there".

We consider these 2 rendering rules:
- nodes are rendered from bottom to top. the last node declared is on top of all the other ones
- a node is either rendered or not. Partial transparency is not considered transparency. So if a
text view renders some text without any background, we still consider that it's "responsible" for
the whole area of its bounding box.

Internally at Waldo, we have built a tool that allows to get the view hierarchy representation on
top of the visual representation of a screen, following the 2 above rules.

You can see the representation if we consider that the nodes from `screen-1` are in the right
order, and that all nodes are rendered (i.e. none are considered transparent):
![all nodes are considered to be rendered](https://user-images.githubusercontent.com/10992081/174875334-5df2a0de-4b05-4391-9a47-c1fcc692da36.png)

And now, the representation if we tag 2 nodes as transparent:
![all nodes are considered to be rendered](https://user-images.githubusercontent.com/10992081/174875335-008dc485-4d33-41d0-8541-895def1a62fb.png)

The goal of this challenge is to tag / reorder / prune nodes from the view hierarchy
programmatically so that the representation of the nodes after processing is consistent with the
visual representation.

## Notes

The way we currently solve for this is to detect elements as visible (meaning they "own" some
pixels on the screen), and mark all elements that are declared AFTER in the view hierarchy to be
considered "transparent".
