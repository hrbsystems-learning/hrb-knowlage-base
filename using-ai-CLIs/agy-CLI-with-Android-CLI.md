
> How to use Android CLI together with agy CLI?

To use Android CLI alongside Antigravity CLI (agy), install the official Android CLI plugin for Antigravity, which equips your agent with the android-cli skill to build, test, and inspect Android apps directly.

1. Install Both CLIs

• Install Android CLI. Download and install it from the Android CLI documentation, then run android info in your terminal to confirm your Android SDK path is detected.
• Install Antigravity CLI (agy). Make sure you have the latest version of Antigravity installed.

2. Connect Android CLI to Antigravity

Install the official plugin from the android-cli-plugin GitHub repository so agy learns how to execute Android CLI commands.
• From your regular terminal:bash
agy plugin install android-cli-plugin@antigravity-plugins-official
Use code with caution.
• Or from inside an active agy session:text
/plugin install android-cli-plugin@antigravity-plugins-official
Use code with caution.
(Alternatively, running android init in your project directory injects core Android CLI skills into detected agent environments.)

3. Add Specialized Android Skills (Optional)

Android maintains an official catalog of task-specific skills (such as Jetpack Compose migration, R8 analysis, or adaptive layouts) on the Android Skills GitHub repository.
• Browse available skills. Run android skills list or search by topic with android skills find "<topic>".
• Install skills. Run android skills add <skill-name> (or android skills add --all)—Android CLI automatically detects Antigravity and places the skills where agy can read them.

4. Example Workflows in agy

Once connected, launch agy in your workspace and prompt it using natural language:
• Project scaffolding. "Create a new Android app using the recommended architecture templates and download any missing SDK components."
• Emulators and deployment. "Start an Android virtual device, build the app, and deploy it."
• UI inspection and debugging. "Capture a screenshot of the current emulator screen and inspect the UI hierarchy to fix the layout alignment."
+10
• 
GitHub
android-cli-plugin
November 15, 2026 — # Android CLI plugin Build Android apps more efficiently with Android CLI. Android CLI is a command-line interface for building An...
• 
Android Developers
Bringing our latest frontier model to Android Developers
# Firebase AI Logic Choose your path: Confirm you have an active Google AI Ultra subscription to use Antigravity, or ensure you ar...
• 
ProAndroidDev
Building Android Apps at the Speed of Thought with Android CLI
August 18, 2026 — Android CLI is Google's modern command line interface designed to give developers and more importantly, AI agents a standardized w...
Show all
        
       
Does agy CLI replace Gemini CLI?

Yes, Antigravity CLI (agy) officially replaced Gemini CLI for individual and consumer accounts on June 18, 2026, though Gemini CLI remains active for enterprise licenses and paid API keys.
According to the Google Developers Blog, Google unified its terminal tooling into Antigravity to share a single multi-agent backend with the Antigravity desktop app.

How the Transition Affects Different Accounts

• Individual & Consumer Plans. Free accounts, Google AI Pro, and Google AI Ultra subscriptions stopped working on Gemini CLI on June 18, 2026, and must use agy.
• Enterprise & Paid API Users. Organizations using Gemini Code Assist Standard or Enterprise licenses—or developers authenticating via paid Gemini API keys—can still use Gemini CLI.
• Newer Models. Google noted in the Gemini CLI Documentation that Gemini CLI is no longer optimized for newer releases like Gemini 4 Argon, which require Antigravity.

Key Differences: agy vs. Gemini CLI


Feature	Antigravity CLI (agy)	Gemini CLI
Runtime & Architecture	Rebuilt in Go; shares the Antigravity server-side agent harness.	Node.js-based open-source CLI.
Execution Style	Asynchronous by default; runs background sub-agents while you continue chatting.	Synchronous single-agent terminal loop.
Extensions	Uses Antigravity plugins (agy plugin install) alongside Agent Skills and MCP.	Uses Gemini CLI extensions (gemini extensions install).
Model Access	Supports multiple models (Gemini, Claude Sonnet/Opus) via agy models.	Tied to Gemini models via Google login or Gemini API keys.
Are you migrating an existing Gemini CLI setup or custom extensions over to agy? Let me know if you'd like help converting your configuration or plugins.

---  

