# Fix responsive chat controls

## Changes
- Rework the composer footer into a stable responsive layout that stays inside the chat sidebar.
- Keep upload and selection actions separate from the model, quality, microphone, and send controls.
- Let the model and quality controls use available width without clipping; wrap them into clean rows when the sidebar narrows.
- Preserve all existing control behavior and styling.

## Verification
- Test the open sidebar at narrow, default, and expanded widths.
- Confirm every option, the microphone, and send button remain visible and clickable without overlapping the canvas.
