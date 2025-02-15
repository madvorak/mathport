## One-shot translation of lean 3 files

This is a template which you can use to quickly play with the translation of snippets of lean 3 code. The procedure is:

1. Clone `https://github.com/leanprover-community/mathport/`
   ```
   git clone https://github.com/leanprover-community/mathport/
   ```
2. get in the folder: `cd mathport`
3. install dependencies `cmake`, `gmp`, `gmp-devel`, `jq` if needed (debian/ubuntu `sudo apt install cmake gmp gmp-devel jq`, mac `brew install cmake jq`, etc)
4. Run `lake exe cache get`
5. Run `make build` (go get some coffee!)
6. Run `make lean3-source`
7. Get a mathport release with `./download-release.sh $my_choice`, where $my_choice = `nightly-2022-12-13-04` works, **or just** `./download-release.sh` to get the latest one automatically.
8. Put Lean 3 code in `Oneshot/lean3-in/main.lean`.
9. Put extra `#align` in `Oneshot/lean4-in/Oneshot.lean`
10. Run `make oneshot`

After the first run, you only have to repeat steps 8-10, unless you want to update mathlib (step 7) or mathport itself (`git pull` and then steps 4-10).

If things work, at the end you should see
`# output is in Outputs/src/oneshot/Oneshot/Main.lean`.
You may need to add `import Mathlib.Mathport.Rename` to this file
before the `#align` commands work.
Also, all you mathlib imports will say `import Mathbin.XYZ`,
and need to be changed to `import Mathlib.XYZ`.
