# Project Roadmap & Task Board

## Progress Tracker
- [x] **Day 1: Repository & Hardware Audit**
  - [x] Clone official MoRA repo (`GroundMoRe`)
  - [x] Inspect README, scripts, and model components (LLaVA, SAM, CLIP, LOC head)
  - [x] Audit RTX 4000 Ada (20 GB VRAM), available disk space, and CUDA drivers
  - [x] Identify required checkpoints and missing dependencies

- [x] **Day 2: Install & Inspect Dependencies**
  - [x] Create isolated Python 3.10 environment (`groundmore` conda env)
  - [x] Install repository's documented dependencies
  - [x] Test imports and resolve package version mismatches (`transformers`, `bitsandbytes`, `torch`)
  - [x] Document CLIP, LLaVA, SAM, and temporal localization head interfaces

- [x] **Day 3: Run the First Inference**
  - [x] Download SAM ViT-H (`sam_vit_h_4b8939.pth`, 2.56 GB)
  - [x] Download MoRA-LISA-7B checkpoint (`groundmore/mora-ft-lisa7b`, 13.9 GB)
  - [x] Run smallest supported inference (1 video, 5 frames, bf16)
  - [x] Profile resources: Peak VRAM = 16.3 GB, Inference Latency = 8.89s
  - [x] Save predicted masks (`pred_masks.npy`, PNGs) and temporal outputs (`loc_probs.npy`)

- [ ] **Day 4: Validate Model Outputs**
  - [ ] Run inference on 5–10 manageable test examples
  - [ ] Verify spatial mask shapes `(T, H, W)` and temporal probability shapes `(T,)`
  - [ ] Inspect visual grounding quality on targeted objects across frames

- [ ] **Day 5: Small Baseline Evaluation**
  - [ ] Run evaluation on a small, fixed test sample
  - [ ] Maintain stable baseline without architectural modifications
  - [ ] Calculate J, F, and J&F metrics
  - [ ] Profile latency, peak VRAM, and log any failure cases

- [ ] **Day 6: Expand Baseline & Test Feasibility**
  - [ ] Evaluate on a larger validation subset within memory and runtime constraints

- [ ] **Day 8: Define Component Interfaces**
  - [ ] Document tensor I/O shapes for frame encoder, LLM, mask decoder, and temporal head
  - [ ] Identify injection points for frame selection modules
  - [ ] Plan modifications for temporal tokenization while keeping fallback selectable

- [ ] **Day 9: Implement Question-Aware Frame Selection**
  - [ ] Implement scoring/selection module inspired by SeViLA
  - [ ] Support configurable selected frame counts
  - [ ] Maintain uniform-sampling fallback
