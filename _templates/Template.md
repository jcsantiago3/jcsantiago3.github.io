<%*
const title = await tp.system.prompt("Note title");

const fileTitle = title
    .toLowerCase()
    .trim()
    .replace(/[^a-z0-9\s-]/g, "")
    .replace(/\s+/g, "-")
    .replace(/-+/g, "-");

await tp.file.rename(`${tp.date.now("YYYY-MM-DD")}-${fileTitle}`);

tR += `---
layout: post
title: ${title}
---
`;
tp.hooks.on_all_templates_executed(async () => { app.workspace.activeLeaf.view.editor.focus(); 
});
%>