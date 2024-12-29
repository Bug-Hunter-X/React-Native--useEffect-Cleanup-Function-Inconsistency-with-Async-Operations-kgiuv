# React Native: useEffect Cleanup Function Inconsistency with Async Operations

This repository demonstrates a common, yet subtle, bug in React Native applications related to the `useEffect` hook and its cleanup function.  The example shows a scenario where asynchronous operations (a `fetch` call and a `setTimeout`) are not consistently cleaned up when the component unmounts, potentially leading to memory leaks or unexpected behavior.

## The Problem
The `useEffect` hook's cleanup function is crucial for canceling any pending asynchronous tasks when a component unmounts. Failure to do so can result in:

* **Memory Leaks:**  Unnecessary data persists in memory even after the component is removed from the UI.
* **Race Conditions:**  Data might be processed or updated after the component is unmounted, leading to unexpected side effects.

## Reproduction
Clone this repository and run the example.  Observe the console logs. You will see that under certain circumstances the cleanup function within `useEffect` does not execute as expected.

## Solution
The solution involves ensuring that the asynchronous operations (fetch, setTimeout) are properly canceled using the cleanup function.