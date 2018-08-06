# Computer Vision Challenge

This challenge offers a view into one of the challenges that we face at Waldo.

The goal that we are pursuing ultimately is to show *meaningful* differences in how screens change
over time in a given mobile application. AND we want to map these visual changes to the underlying
boxes that they correspond to.

In other words, we use the pixels to understand that something changed on screen, but we report
by scoping to the box that we think explains the change.

## Submit

Please add [@laurentsigal](https://github.com/laurentsigal) as a contributor to your github repository.

Otherwise you can simply host the code anywhere and give us a link to the zip file.

Do not make your repository public.

## Input

In order to do that, we have 2 signals that we can use:
- the boxes of what's represented on screen: e.g. [before/boxes.xml](https://github.com/waldoapp/cv-challenge/blob/master/before/boxes.xml).
- the screenshot: e.g. [before/screenshot.png](https://github.com/waldoapp/cv-challenge/blob/master/before/screenshot.png).

These 2 signals are extracted from the mobile device at the same time, and therefore correspond
to the same state.

## Goals

In this challenge, you are given the 2 states of the same screen, extracted from 2
versions of the same application that are approximately 6 months apart, denoted by
`before` and `after`.

Objectives:
- Match every pixel to a box. For instance, it should be recognized that the background is
covering the whole screen, and therefore not attributed in pieces to the smaller boxes
covering the area
- Explain the visual differences between the 2 screenshots using this high level
abstraction of boxes. For instance, the change for the field `email` should be decomposed into
the fact that the text was translated down (attributed to the corresponding box) while the
background did not change.

What we are looking for:
- the ideas and implementation that you used. We believe this should not be a lot of code
if you leverage all the existing libraries that are at your disposal.
- the ability to break down the problem into the 2 pieces, i.e. if the solution would be able
to match pixels to boxes even if given a single version of the screen.
- the structure that you will use to scope and report these differences.
