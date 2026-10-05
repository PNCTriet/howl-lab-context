# Virtual Visit handoff — 2026-10-05 ~14:29 (Usage ~2%)

## Live
- https://virtual-visit-selfhost.vercel.app
- https://virtual-visit-mvp.vercel.app → https://zep.us/play/ZX5BrG
- Repo: https://github.com/PNCTriet/virtual-visit-selfhost

## Commits (pull these next session)
- **`243f519`** — latest WIP; body has full DONE/TODO
- `3488182` — landing Enter + MacBook/iPhone posters
- `9020bc7` — room fullscreen; MacBook static photo
- `13fb826` — Phaser + Tiled + sprites

## DONE (243f519)
- Landing: no room input, Enter room only
- Desktop one viewport; MacBook + overlapping iPhone
- Mobile &lt;768: iPhone only, above copy
- /room fullscreen; name prompt if open direct
- Landing ready for video; still using static posters
- Demo modes `?demo=wide` and `?demo=phone` (5 NPCs, 10s; phone has finger joystick)
- Removed dt/fps debug

## TODO next session
1. Run `scripts/record-demo-frames.cjs`
2. ffmpeg → room-mac / room-phone webm+mp4+poster; wire `MAC_CLIP`/`PHONE_CLIP` in `components/DevicePreview.tsx`
3. QA clips
4. Update README
5. Verify prod (redeploy if needed)

## Shots
`/workspace/virtual-visit-selfhost-shots/v3/` (posters)
