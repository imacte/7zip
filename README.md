# 7-Zip on GitHub
7-Zip website: [7-zip.org](https://7-zip.org)

## This copy

A mirror of the upstream 7-Zip sources, plus the two things the upstream source
tree does not contain:

* `Lang/` - the language files of the official 26.04 package. They ship inside
  the installer (`https://www.7-zip.org/a/7z2604.exe`), not in the sources; keeping
  them here makes a source build a complete 7-Zip (without them the file manager
  and the console fall back to their built-in English text). They are also the
  language files of the RoxaZip payload.
* `.github/workflows/build.yml` - builds the Windows binaries (`7z.dll`, `7z.exe`,
  `7zFM.exe`, `7zG.exe`, `7z.sfx`, `7zz.exe`) for x86, x64 and ARM64, and `7zz`
  for Linux with gcc and clang; each job runs an archive round trip as a smoke
  test and uploads the binaries together with `Lang/` and the text files of the
  package as an artifact.

The object and output directories of the makefiles are ignored, see `.gitignore`.
