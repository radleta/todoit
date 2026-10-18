---
tags: [todoit-expert/fun-principles]
summary: "The transcript principles that define fun for todoit (impact, reward, challenge, fantasy, people differ) and the rule each sets for an interaction"
---

# Fun principles

Test every todoit interaction choice against the principles of the game-design transcript at [`scratch/repo-setup/fun.md`](../../../scratch/repo-setup/fun.md), a video about making a button fun to press. That includes a gesture, a bubble effect, the empty state and a new feature. Do not test it against a personal sense of what feels playful. Each principle sets one rule:

| Principle | What the transcript means | Rule for a todoit interaction |
|---|---|---|
| **Impact** | Changing your surroundings gives "a feeling of control and power", best "quickly and without a lot of effort". Having none "feels like a waste of time", and "lasting consequences are more fun". | Every action visibly moves the bubble field at once, for one gesture. The empty state has something to press. A popped todo lives on under the done filter, so a pop never looks undone or lost. |
| **Reward** | "Acoustic rewards and eye candy": sound, particles, wobble, shake. "Lasting rewards tend to feel more valuable", and a short delay makes a reward more desirable. Randomness excites, but the transcript calls randomized rewards "an abusive gambling game" and "morally questionable". | Popping gets the strongest sound and eye candy in the app. A delay before the reward is a short animation and never holds back the todo's state change. Randomness stays cosmetic (pitch, particle colour, spread) and never varies what an action earns. |
| **Challenge** | Too much is "stressful and frustrating" and too little is "boring". "Attaching rewards to challenges is a sensible thing to do", and a good challenge is fair and gives "plenty of feedback on how well you're doing". | The challenge is the visitor's own tasks, never the controls: a pop needs no aim or timing, because impact wants effects without effort. Reward follows the challenge: completing earns more than adding, and deleting earns less than completing, so discarding a task never feels like finishing it. The visitor can always see how they are doing, such as how many todos are active and how many are done. |
| **Fantasy** | Framing alone changes the feel "even though the gameplay is completely the same": the same button becomes "the master button in the fun spaceship". | Bubbles are a frame, and choosing the app's look is choosing a fantasy. Wording and the empty state stay inside the chosen frame. |
| **People differ** | "Different people want different challenges different rewards different fantasies", and "if somebody doesn't like space you might even be better off keeping it abstract". | No effect is forced on anyone: sound can be muted, and motion follows the system's reduced-motion setting. A theme never gets in the way of plain use. An abstract look is a valid choice, because a strong theme loses visitors who dislike it. |

## Decisions

- Fun means the transcript's principles, applied in its order, not a looser sense of "playful", because the user set the transcript as the definition of fun ([`todoit-v1` epic `## Decisions`](../../../scratch/issues/todoit-v1.md), settled by the [`fun-principles` spike](../../../scratch/issues/fun-principles.md)).
