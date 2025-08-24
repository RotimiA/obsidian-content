<%*
const title = await tp.system.prompt("Title");
if (!title) { throw new Error("Title is required"); }
const date = tp.date.now("YYYY-MM-DD");
const slug = title.toLowerCase().replace(/[^a-z0-9]+/g,"-").replace(/(^-|-$)/g,"");
await tp.file.rename(slug);
-%>
---
title: "<%= title %>"
slug: "<%= slug %>"
date: <%= date %>
status: draft
---

# <%= title %>