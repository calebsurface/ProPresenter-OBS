# ProPresenter-OBS

Uses the ProPresenter Stage Display websocket **or** OpenAPI to feed current slide text into a OBS browser source lower third.

The original code was from https://github.com/cgarwood/ProPresenter-vMix and made for vMix.

## Configuration

Rename config.js.example to config.js and update the values to match your environment.

### API Type Selection

Choose which ProPresenter API to use:

**Option 1: Stage Display API (WebSocket)** - Default, Most Compatible
- Set `api_type: 'stagedisplay'` in config.js
- **Works with ProPresenter 6, ProPresenter 7 (all versions), and ProPresenter 7.9.1+**
- Most widely compatible option - works with all ProPresenter versions
- In ProPresenter: Enable Network and Stage Display App under preferences/settings
- Set a password under Stage Display App
- Use the port listed under Enable Network (NOT the Stage Display App port)
- Use the password from Stage Display App in config.js

**Option 2: OpenAPI (HTTP REST)** - Modern Alternative for ProPresenter 7.9.1+
- Set `api_type: 'openapi'` in config.js
- **Requires ProPresenter 7.9.1 or newer** - will not work on older versions
- In ProPresenter: Enable Network under settings
- No password required - simpler setup
- Uses HTTP streaming for real-time updates
- Uses the official REST API provided by ProPresenter
- Best choice if you're running ProPresenter 7.9.1+ and want simpler configuration

**Which should I use?**
- Use **Stage Display** (default) if you're on ProPresenter 6 or any ProPresenter 7 version before 7.9.1
- Use **Stage Display** if you want maximum compatibility
- Use **OpenAPI** if you're on ProPresenter 7.9.1+ and prefer no password setup

### OBS Setup

In OBS, add a new browser source, check "Local File", navigate to index.html, then set width, height, and FPS to match your stream settings. Edit stylesheet.css to customize your lower thirds setup.

### Filtering Slides

Set the slide notes to `no-obs` on a slide to prevent it from being sent to OBS (useful for slides with more text than you would want in a lower third).
