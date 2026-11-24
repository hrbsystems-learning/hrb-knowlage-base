
I use Junie CLI from JetBrains. Is it possible to integrate Android CLI and all the skills it provides into Junie CLI?

Yes, you can integrate Android CLI and its entire skill library into Junie CLI because both follow the open SKILL.md Agent Skills standard.
While android skills add defaults to Antigravity's directory (~/.gemini/antigravity/skills), Junie CLI automatically reads skills from ~/.junie/skills/, <projectRoot>/.junie/skills/, and the cross-agent .agents/skills/ folder.

1. Install All Android Skills into Junie CLI

You can populate Junie's global skills folder using android skills add or by pointing Junie's configuration directly to the shared skills directory:
• Option A: Download via Android CLI and copy to Junie (Global).
Run the Android CLI to download all official skills, then copy them into Junie's global directory:bash
android skills add --all
mkdir -p ~/.junie/skills
cp -r ~/.gemini/antigravity/skills/* ~/.junie/skills/
Use code with caution.
• Option B: Point Junie directly to your existing skills folder.
To avoid duplicating folders and keep android skills update --all in sync across both agy and Junie, add the path to your Junie config.json skill-locations field or launch Junie with the --skill-location flag:bash
junie --skill-location ~/.gemini/antigravity/skills
Use code with caution.
• Option C: Project-level sharing (.agents/skills/).
If you install skills into <projectRoot>/.agents/skills/, Junie CLI automatically detects and loads them for that workspace.

2. Add the Core android-cli Skill

To ensure Junie knows how to invoke android terminal commands (like android emulator, android sdk, or android device), include the core android-cli skill from the android-cli-plugin repository in your .junie/skills/ folder as well. Because android is a standard shell binary in your PATH, Junie CLI can execute those commands directly once instructed by the skill.

3. Pair with JetBrains' Native Android Integration

Alongside Google's Android CLI skills, JetBrains provides native Android tooling for Junie described in the Junie Android Development Docs:
• Junie IDE Plugin. Running Junie CLI alongside Android Studio (with the Junie plugin installed) exposes built-in IDE actions for logcat, Compose previews, and device state.
• android-engineer Extension. Run /extensions inside Junie CLI to install android-engineer, which adds JetBrains' own Android QA subagent and Mobile MCP server alongside your imported Google Android skills.
Would you like to set this up globally across all projects via Junie's config.json or per-repository so your team shares the skills? Let me know your OS and setup preference so I can give you the exact configuration snippet.
+3
• 
JetBrains
Android development with Junie | Junie Documentation
November 19, 2026 — Junie CLI extension that adds senior-engineer skills, a QA subagent, and the Mobile MCP server for UI interaction on top of the bu...
• 
Android Developers
Device Streaming and Android skills - available in Android CLI
Managing skills across projects and individual agent directories is pretty straightforward with Android CLI: skills update --all; ...
• 
JetBrains
Agent skills | Junie Documentation
August 20, 2026 — Agent skills are folders with instructions, templates, scripts, and reference materials that provide Junie with task-specific cont...
Show all
