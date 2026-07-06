# Creating and Solving a Hackers Challenge with Claude

Slides and speaker script for a DefCon talk about building **"The Hackers Challenge"**, a
complete CTF competition, using **Claude** and **Claude Code**.

The talk walks through what it was like to build 15+ challenges across 4 categories in 4 weeks
with AI assistance: how the development bottleneck shifted from *writing* code to *testing and
validating* AI output, what worked, what didn't, and the lessons learned along the way.

## Contents

| File | Description |
| --- | --- |
| [`hackers_challenge_dc435.pptx`](hackers_challenge_dc435.pptx) | The presentation slides. |
| [`presentation_script.md`](presentation_script.md) | The full speaker script (Markdown). |
| [`presentation_script.md.docx`](presentation_script.md.docx) | The speaker script as a `.docx` export. |
| [`docs/`](docs/) | Supporting material: an example challenge write-up and its media assets. |

## What the talk covers

- The origin story: organizing a CTF with limited coding time
- The LLM journey and costs (local models, Gemini, Claude Free, Claude Code)
- How the development workflow changed with AI assistance
- The challenges built: SyncFlow (multiplayer), GraphQL, and Matrix-themed encoding challenges
- CTFd modifications, Claude Code frustrations, and key lessons learned

## Example challenge

[`docs/example-challenge-neo-sees-the-code.md`](docs/example-challenge-neo-sees-the-code.md)
documents one of the encoding challenges, *"Neo Sees the Code"*, a Matrix-style video that hides
Morse code in falling green characters. The related media assets (`matrixrain.mp4`,
`morpheusmessage.wav`, `kungfu.svg`, `whiterabbit.svg`) live alongside it in [`docs/`](docs/).
