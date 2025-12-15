# clinerules

## Installation

### Interactive multiselect

```bash
(printf "\nSelect rules (comma/space separated, 'a' for all):\n"; printf "  1) core\n  2) shell\n"; read -r c; [ -z "$c" ] && printf "Cancel\n" && exit; case "${c}" in *[aA]*) s="1 2";; *) s=$(echo "$c" | tr ', ' '\n' | grep -E '^[1-2]$' | sort -u);; esac; [ -z "$s" ] && printf "No valid choices\n" && exit; t=$(mktemp -d); git clone -b main --depth 1 https://github.com/shimarulin/clinerules.git "$t"; mkdir -p .clinerules; for v in $s; do case $v in 1) d=core;; 2) d=shell;; esac; cp -r "$t/clinerules_$d/." .clinerules/ 2>/dev/null; done; rm -rf "$t"; echo -n "Selected: "; for v in $s; do case $v in 1) echo -n "core ";; 2) echo -n "shell ";; esac; done; printf "\nDone\n")
```

**Readable version:**

```bash
(
  printf "\nSelect rules (comma/space separated, 'a' for all):\n"
  printf "  1) core\n  2) shell\n"
  read -r c
  [ -z "$c" ] && printf "Cancel\n" && exit

  case "${c}" in
    *[aA]*) s="1 2";;
    *) s=$(echo "$c" | tr ', ' '\n' | grep -E '^[1-2]$' | sort -u);;
  esac

  [ -z "$s" ] && printf "No valid choices\n" && exit

  t=$(mktemp -d)
  git clone -b main --depth 1 https://github.com/shimarulin/clinerules.git "$t"
  mkdir -p .clinerules

  for v in $s; do
    case $v in
      1) d=core;;
      2) d=shell;;
    esac
    cp -r "$t/clinerules_$d/." .clinerules/ 2>/dev/null
  done

  rm -rf "$t"
  echo -n "Selected: "
  for v in $s; do
    case $v in
      1) echo -n "core ";;
      2) echo -n "shell ";;
    esac
  done
  printf "\nDone\n"
)
```

**Features:**

1. **Multi-selection support** - Select multiple options using commas or spaces
2. **'a' alias for all** - Type 'a' or 'A' to select both options
3. **Input validation** - Only accepts numbers 1-2
4. **Duplicate prevention** - Removes duplicate selections automatically
5. **Empty input handling** - Cancels on empty input
6. **Single repository cloning** - Efficient one-time clone
7. **Automatic cleanup** - Removes temporary directory
8. **Directory creation** - Creates .clinerules if missing
9. **Error suppression** - Ignores copy errors silently
10. **Progress feedback** - Shows selected options upon completion
11. **Cross-shell compatibility** - Works in both bash and zsh
12. **Merge functionality** - Combines both rule sets into single directory
13. **Smart parsing** - Handles mixed separators (commas, spaces, or both)
14. **Case-insensitive 'a'** - Both 'a' and 'A' work for selecting all
15. **Clear output** - Shows "Selected: core shell" when both are chosen

**Implementation details:**
- Uses `mktemp` for secure temporary directory creation
- Shallow clone (`--depth 1`) for faster downloads
- Preserves existing `.clinerules` content when copying
- Returns meaningful exit codes
- Runs in subshell to avoid affecting current shell environment



### Interactive select

```sh
(echo "\nSelect:"; echo "  1) strict\n  2) memo"; read c; case $c in 1)v=core;;2)v=shell;;3)v=ts;;4)v=go;;*)echo "Cancel"; exit;; esac; t=$(mktemp -d); git clone -b main --depth 1 https://github.com/shimarulin/clinerules.git $t; cp -r $t/clinerules_$v/. .clinerules; rm -rf $t; echo "$v Done")
```

### Installation command template

```sh
CLR_VARIANT=<variant> CLR_TMP=$(mktemp -d)  && git clone -b main --depth 1 https://github.com/shimarulin/clinerules.git $CLR_TMP && cp -r $CLR_TMP/clinerules_$CLR_VARIANT/. .clinerules && rm -rf $CLR_TMP
```

#### Strict rules

```sh
CLR_VARIANT=strict CLR_TMP=$(mktemp -d)  && git clone -b main --depth 1 https://github.com/shimarulin/clinerules.git $CLR_TMP && cp -r $CLR_TMP/clinerules_$CLR_VARIANT/. .clinerules && rm -rf $CLR_TMP
```
