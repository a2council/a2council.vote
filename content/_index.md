---
title: "Home"
type: landing

sections:
  - block: resume-biography
    content:
      username: admin
      text: "🐈 Welcome to the **community-run** Ann Arbor City Council voting chart database! 🐈"
    design:
      spacing:
        padding: ["2rem", 0, "1rem", 0]
      avatar:
        size: medium
        shape: circle
  - block: collection
    content:
      title: Recent Charts
      count: 10
      filters:
        folders:
          - post
    design:
      view: date-title-summary
      spacing:
        padding: ["1rem", 0, "4rem", 0]
---
