---
description: "Cancel active Ralph Wiggum loop"
allowed-tools: ["Bash"]
hide-from-slash-command-tool: "true"
---

# Cancel Ralph

```bash
python -c "
import sys
from pathlib import Path
state_file = Path('.claude/ralph-loop.local.md')
if state_file.exists():
    content = state_file.read_text()
    import re
    match = re.search(r'iteration:\s*(\d+)', content)
    iteration = match.group(1) if match else 'unknown'
    print(f'FOUND_LOOP=true')
    print(f'ITERATION={iteration}')
else:
    print('FOUND_LOOP=false')
"
```

Check the output above:

1. **If FOUND_LOOP=false**:
   - Say "No active Ralph loop found."

2. **If FOUND_LOOP=true**:
   - Use Bash: `python -c "from pathlib import Path; Path('.claude/ralph-loop.local.md').unlink()"`
   - Report: "Cancelled Ralph loop (was at iteration N)" where N is the ITERATION value from above.
