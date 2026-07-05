Goal
- Fix unzip-to-7z wrapper so that the 7-zip backend (7z2601) behaves as good as the p7zip backend for ZIP filename encoding in legacy archives (see https://github.com/clsty/zip-encoding-test/blob/e7aa4499f928c241d2eec5ebf3ceacae41d4f452/test-report.md )
Constraints & Preferences
- Do NOT modify 7-zip source code (use bash wrapper + environment variables)
- Do NOT use Python (not universally available on Linux)
- 7-zip behavior can be controlled via parameters/env vars
- System locale: zh_CN.UTF-8
- Test archives in https://github.com/clsty/zip-encoding-test
