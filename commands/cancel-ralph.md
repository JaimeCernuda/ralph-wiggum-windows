---
description: "Cancel active Ralph Wiggum loop"
allowed-tools: ["Bash"]
hide-from-slash-command-tool: "true"
---

# Cancel Ralph

```!
if (Test-Path .claude\ralph-loop.local.md) {
  $content = Get-Content .claude\ralph-loop.local.md -Raw
  if ($content -match 'iteration:\s*(\d+)') {
    $iteration = $Matches[1]
    Write-Host "FOUND_LOOP=true"
    Write-Host "ITERATION=$iteration"
  } else {
    Write-Host "FOUND_LOOP=true"
    Write-Host "ITERATION=unknown"
  }
} else {
  Write-Host "FOUND_LOOP=false"
}
```

Check the output above:

1. **If FOUND_LOOP=false**:
   - Say "No active Ralph loop found."

2. **If FOUND_LOOP=true**:
   - Use Bash: `Remove-Item .claude\ralph-loop.local.md -Force`
   - Report: "Cancelled Ralph loop (was at iteration N)" where N is the ITERATION value from above.
