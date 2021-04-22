
#### 1) Intial state - Example API key(s) already in 'ExampleClass.cs'


#### 2) Both the following initially run and return no results.

```
.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInRulesAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet

.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInGlobalAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet
```

#### 3) Update 'ExampleClass.cs' to add another like with an API key. Save but don't stage or commit.


#### 4) Both the below now run but 'CsInGlobalAllowlist' DOES highlight the 'Leak' in the unstaged and uncommitted file, when it's expected it shouldn't

```
.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInRulesAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet

.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInGlobalAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet
```


#### 5) Stage 'ExampleClass.cs' file within repo


#### 6) Both now run but 'CsInGlobalAllowlist' still DOES highlight the 'Leak' in the unstaged and uncommitted file, when it's expected it shouldn't

```
.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInRulesAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet

.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInGlobalAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet
```


#### 7) Copy 'ExampleClass.cs' into a new file. Save but don't stage or commit.


#### 8) Both now run but neither highlights the 'Leak' in the new, unstaged and uncommitted file, when I'd expect it should

```
.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInRulesAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet

.\bin\gitleaks-windows-amd64.exe --repo-config-path ".gitleaks.CsInGlobalAllowlist.toml" --redact --unstaged --format=json --leaks-exit-code=0 --quiet
```

