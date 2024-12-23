# Expo Linking.getInitialURL() Returns Null Intermittently

This repository demonstrates a bug where `Linking.getInitialURL()` in Expo returns `null` even when the app is launched with a deep link. The issue appears to be related to the timing of the method call relative to app initialization.

## Bug Description

The `Linking.getInitialURL()` method is used to retrieve the initial URL that launched the app. However, in some cases, it returns `null`, even when the app was clearly launched via a deep link. This is inconsistent and makes it difficult to handle deep links reliably.

## Reproduction

1. Clone this repository.
2. Run the app using `expo start`.
3. Open a deep link to the app (e.g., using a browser).
4. Observe the output in the console.  You might need to run it several times to see the `null` output.

## Solution

The solution is to use `Linking.addEventListener` to listen for incoming URL changes. This approach allows you to handle deep links regardless of whether `getInitialURL()` returns `null`. See the `bugSolution.js` file for the implementation.

## Additional Notes

This issue seems to be non-deterministic and may be related to the app's loading time or underlying system behavior.  Always handle potential `null` responses gracefully.