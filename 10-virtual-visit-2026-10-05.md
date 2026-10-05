# Virtual Visit — cập nhật 2026-10-05

## Live
- ZEP gateway: https://virtual-visit-mvp.vercel.app → https://zep.us/play/ZX5BrG
- Self-host (no ZEP): https://virtual-visit-selfhost.vercel.app
- Repos: PNCTriet/virtual-visit-mvp, PNCTriet/virtual-visit-selfhost

## Self-host stack
- Next.js + Supabase Realtime (HOWLSLAB `jexjlaqblulgfjcssekb`), channel `virtual-visit:room:<id>`
- Env: NEXT_PUBLIC_SUPABASE_URL + NEXT_PUBLIC_SUPABASE_ANON_KEY
- main tại thời điểm checkpoint: `688c05b` (canvas MVP)
- WIP v2 (DEVIN ~60%): Phaser 3 + Kenney tileset/sprites + Tiled office.tmj + MacBook mock + joystick; Founder yêu cầu push partial vì Usage ~90%

## Quyết định sản phẩm
- Free ZEP lộ branding; Pro ~$50/10 user chỉ custom `zep.us/@…`; white-label thật cần Enterprise hoặc tự host
- Self-host MVP: chỉ map + avatar walk + sync; không voice

## Founder note 14:12
Usage weekly ~90% — giữ checkpoint, DEVIN push WIP sớm.
