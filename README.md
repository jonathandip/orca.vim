# Vim syntax for Orca

This project provides syntax highlighting for the [Orca quantum chemistry](https://orcaforum.kofo.mpg.de/app.php/portal) program compatible with the Orca 6.1.1 release (and backwards compatible with 5.0.2).


## Syntax highlighting

Add the file in `syntax/orca.vim` to your *vim* runtime directory (*e.g.* `~/.vim/syntax/orca.vim`).


## File type detection
### Vim
Add these lines to your *vim* runtime directory in `ftdetect/orca.vim` to use the Orca syntax highlighting for all files ending in `.orca` and files named `orca.inp`.

```vim
" For vim >= 8
au BufRead,BufNewFile *.orca set filetype=orca
au BufRead,BufNewFile orca.inp set filetype=orca
```
### Neovim
Add these lines to your *lua* configuration files to use the Orca syntax highlighting for all files ending in `.orca` and files named `orca.inp`.
```lua
-- For neovim >= 0.8
local create_autocmd = vim.api.nvim_create_autocmd
local events = {"BufRead", "BufNewFile"}
create_autocmd(events, { pattern = {"*.orca"}, command = [[ set filetype=orca ]]})
create_autocmd(events, { pattern = {"orca.inp"}, command = [[ set filetype=orca ]]})
```


## Changelog

### 6.1.1 (2026-04-27)

Added syntax coverage for all new features introduced between ORCA 5.0.2 and ORCA 6.1.1.

**New DFT functionals**
- r2SCAN-based hybrids and double-hybrids: `R2SCANH`, `R2SCAN50`, `PR2SCAN50`, `PR2SCAN69`, `WPR2SCAN50`, `KPR2SCAN50`, `R2SCAN-CIDH`, `R2SCAN-QIDH`, `R2SCAN0-DH`, `R2SCAN0-2` (including `RI-` and `DLPNO-` variants)
- Composite 3C methods: `WB97X-3C`, `B3LYP-3C` (including `QM/MM` variants)
- Revised dispersion: `WB97M(2)`, `WB97X-D4REV`, `WB97M-D4REV`, `REVDSD-PBEP86-D4`, `REVDOD-PBEP86-D4`
- Non-covalent double-hybrid: `B2NC-PLYP`

**New wavefunction methods**
- `NEVPT3`, `ICE-FR-NEVPT2`, `CCSDTQ`, `RPAC`
- `UHF-IP-EOM-CCSD`, `UHF-EA-EOM-CCSD`, `UHF-STEOM-CCSD`

**New optimizer and structure keywords**
- GOAT modes: `GOAT-ENTROPY`, `GOAT-EXPLORE`, `GOAT-REACT`, `GOAT-DIVERSITY`, `GOAT-COARSE`
- `RIGIDBODYOPT`, `S-IDPP`

**New docking keywords**
- `QUICKDOCK`, `NORMALDOCK`, `COMPLETEDOCK`
- `DOCK(GFN-FF)`, `DOCK(GFN0-XTB)`, `DOCK(GFN1-XTB)`, `DOCK(GFN2-XTB)`

**New analysis and SCF keywords**
- `DELTASCF`, `LEANSCF`, `MIXGUESS`, `BUPO`, `AUTOTRAH`
- `MBIS`, `RESP`, `DRACO`, `ADLD`, `ADEX`, `DBOC`, `VCD`, `SMD18`, `COVALED`

**New basis sets**
- `vDZP` (for wB97X-3C), `CRENBL`, `CRENBL-ECP`
- HGBS family (hydrogenic Gaussian): `HGBS-5/7/9`, `HGBSP1/2/3-5/7/9`, `AHGBS-5/7/9`, `AHGBSP1/2/3-5/7/9`
- pcX family (core X-ray spectroscopy): `PCX-1/2/3/4`, `AUG-PCX-1/2/3/4`
- pcH family (hyperfine coupling): `PCH-1/2/3/4`, `AUG-PCH-1/2/3/4`

**New block directives**
- `%goat`, `%docker`, `%solvator`, `%casresp`, `%frag`, `%casdft`, `%mcd`

### 5.0.2 (initial release)

Initial syntax highlighting rules for ORCA 5.0.2.


## Similar projects

- [mrymtsk/orca-vim](https://github.com/mrymtsk/orca-vim) by Toshiki Murayama ([@mrymtsk](https://github.com/mrymtsk))


## License

Licensed under the Apache License, Version 2.0 (the “License”);
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an *“as is” basis*,
*without warranties or conditions of any kind*, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

Unless you explicitly state otherwise, any contribution intentionally
submitted for inclusion in this project by you, as defined in the
Apache-2.0 license, shall be licensed as above, without any additional
terms or conditions.
