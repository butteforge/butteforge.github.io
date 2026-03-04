---
layout: default
title: Meetings
permalink: /activity/meetings.html
---

# Meetings

A record of team meetings, decisions, and progress.

---

## February 28, 2026 - HC-SR04 Integration & Team Progress

During our first week, we discovered that the HC-SR04 sensor used by Paul
McWhorter in his tutorial worked directly with the Raspberry Pi at 3.3V. We
wanted to follow the same approach. However, although our sensors look
identical, they did not operate correctly at that voltage.

After testing and investigating, we found that our units require a 5V supply.
This means the ECHO signal outputs 5V, and the Raspberry Pi cannot safely
accept that voltage on its GPIO pins. In the final minutes of our previous
meeting, we built a voltage divider and verified the solution - it worked.

Today, we spent over two hours working on the code, and all three teams, using
the voltage divider circuits, were able to test the sensor and extend the
program's functionality. Each group brought their solution to a working state
- this is a significant step forward.

### Code Abstraction Tiers

We recognized the need for different levels of code abstraction. At this stage,
a three-tier model seems most reasonable:

- **Tier 0** - Structural code, as simple as possible. The lowest possible
  entry barrier for future members who join us.
- **Tier 1** - Object-oriented code with error handling, still based on the
  mtech_gpio wrapper.
- **Tier 2** - Direct work with lgpio, full control over the hardware layer.

### Open Questions

Important organizational questions also emerged:

- What repository standard should we adopt?
- What should its structure look like?
- How do we name variables, functions, and classes?
- Which coding standards do we choose as a team?

These are questions we will need to answer together.
