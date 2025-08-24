<%*
const title = await tp.system.prompt("Title");
if (!title) { throw new Error("Title is required"); }
const date = tp.date.now("YYYY-MM-DD");
const slug = title.toLowerCase().replace(/[^a-z0-9]+/g,"-").replace(/(^-|-$)/g,"");
await tp.file.rename(slug);


tR += `---\n`;
tR += `title: "${title.replace(/"/g,'\\"')}"\n`;
tR += `slug: "${slug}"\n`;
tR += `date: ${date}\n`;
tR += `status: draft\n`;
tR += `---\n\n`;
tR += `# ${title}\n`;
%>
# <%= title %>