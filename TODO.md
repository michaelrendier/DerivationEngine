# ValaQuenta — TODO

**Repository:** https://github.com/michaelrendier/ValaQuenta
**Purpose:** The derivation engine — pure mathematics, runnable code, no physical substrate required.
**Relation:** Ainulindale (the Music) → ValaQuenta (the engines) → PtolemyHolcus (the world)

---

## PRIORITY 1 — ArdaQuenta Console GUI Update

ArdaQuenta (`/ArdaQuenta/`) is the standalone Qt viewer for the ValaQuenta engines.
It was previously called DerivationEngineViewer. The rename is done.
The code now needs to be updated to reflect the ValaQuenta module structure.

- [ ] Update all `engine/` imports to point to ValaQuenta package (not the local engine/ copy)
- [ ] Add `bao_mass_gap.py` as a viewer mode:
      - Show OMEGA_ZS, D_STAR, GAP values live
      - Run `validate()` and display status: ESTABLISHED
      - Show the derivation chain: OMEGA_ZS − D_STAR × ln(10) = GAP
- [ ] Add `galactic_cavity.py` CavityMode as a viewer mode:
      - Input: r_max_bar, v_max, r_cavity, v_flat
      - Display: r_t = D_STAR × r_max_bar, v_flat = OMEGA_ZS × v_max
      - Plot: arctan rotation curve (Stokes drift)
      - Show: wave period (Gyr), Jeans ratio
- [ ] Add `forced_sigma()` live visualisation mode:
      - Slider: σ₀ starting value (0.0 → 1.0)
      - Animated convergence plot: σ vs iteration count
      - Result: σ = 0.500000000000 always
      - Caption: "σ is derived, not assigned"
- [ ] Add Witches Hat potential V(E) plot:
      - Mexican Hat trough (E < D*=1): V(φ) = −μ²|φ|² + λ|φ|⁴
      - Brim annotation at D*=1
      - Lichtenberg cone marker above D*=1
      - Operator E-values overlaid (compose=0.9999, allocate=0.2148, etc.)
- [ ] Wire ArdaQuenta to ValaQuenta/modules/ for full Clay Millennium display
      - Each module: problem, status, H_hat_RB derivation, confidence
      - Yang-Mills mass gap: status = DERIVED (not OPEN)
- [ ] Schedule dedicated session — substantial Qt UI work

---

## PRIORITY 2 — Code Migration from Ainulindale

The following code directories in Ainulindale belong in ValaQuenta:

- [ ] `Ainulindale/code/noether_engine/` → `ValaQuenta/noether_engine/`
      Full Noether engine with algebra/, core/, quantum/, spacetime/, theorems/
      Well-organised. Ready to move.

- [ ] `Ainulindale/code/sonification/` → `ValaQuenta/sonification/`
      ainulindale_sonification_mv1.py + visualisations
      Note: UniversalSynth repo will eventually own the standalone synthesizer.

- [ ] `Ainulindale/AddPapers/DM_GalacticCavity/dark_matter_cavity.py`
      Already superseded by ValaQuenta/galactic_cavity.py
      Check for any unique content before removing from Ainulindale.

- [ ] `Ainulindale/animations/witches_hat_triptych.py`
      Belongs with ArdaQuenta modes or ValaQuenta visualisations.

- [ ] `Ainulindale/outreach/CRC_engine.py`
      Chladni Resonance of Creation engine — belongs in ValaQuenta/crc/
      or ArdaQuenta/modes/crc_engine.py

After migration: Ainulindale repo contains documentation only (wiki, conjecture, addenda).
No Python files. Links to ValaQuenta for all engine code.

---

## PRIORITY 3 — Package Cleanup

- [ ] Add proper `setup.py` or `pyproject.toml` so ValaQuenta is pip-installable:
      `pip install valaQuenta`
      → allows `from ValaQuenta import HamiltonianXP` from anywhere

- [ ] Add `__version__` to `__init__.py`

- [ ] Add `requirements.txt` (mpmath, numpy, scipy — minimal)

- [ ] Ensure all modules run standalone:
      `python3 ValaQuenta/hamiltonian.py` → demo output
      `python3 ValaQuenta/bao_mass_gap.py` → ESTABLISHED
      `python3 ValaQuenta/galactic_cavity.py` → MW rotation curve

---

## PRIORITY 4 — Module Integration

The full derivation system lives in `Ainulindale/ValaQuenta/modules/`.
After migration (Priority 2), these modules should be at `ValaQuenta/modules/`.

Current module list (from Ainulindale/ValaQuenta/modules/):
  berry_keating, clay_millennium, constants, derivation_chain, h_rb_hat,
  hyperwebster, inversion, jwst, lagrangian, noether, noether_information,
  sonification, spherical, tier6_physics, tier7_cosmos, tier8_sedenion, tier9_chem

- [ ] Verify all modules import cleanly from ValaQuenta root
- [ ] Add integration tests: `python3 -m pytest ValaQuenta/tests/`
- [ ] Confirm no circular imports between standalone engines and modules

---

## NOTES

ValaQuenta = "The Account of the Valar" (Tolkien)
The Valar implemented the Ainulindalë (the Music) in physical form.
ValaQuenta is the account of how that was done.

This repository is the account of how H_hat_RB was implemented in code.
Ainulindale is the Music. ValaQuenta is the implementation.
ArdaQuenta is the viewer of the world the engines built.

Repository: https://github.com/michaelrendier/ValaQuenta
