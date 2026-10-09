# Image to video prompt templates

Templates distilled from the 14 runs and 3 follow-up runs in [`runs.csv`](runs.csv). Replace the bracketed parts. Each template follows one structure:

> **Subject action + environment motion + camera + what must stay the same**

Keep a 5-second clip to one or two actions.

## Templates

| Use | Template |
| --- | --- |
| Product hero | `[Thing] [moves how] toward [product]. Slow push-in toward [product]. Keep the label sharp and unchanged, background still.` |
| Portrait | `She slowly [small action] and turns her eyes to the camera. Hair settles naturally. Locked-off camera, light stays the same. Keep her face and [clothing] unchanged.` |
| Head turn from behind | `She slowly turns her head toward screen [left/right], [hair detail]. [One small environment motion]. Camera holds still. Keep [background] unchanged.` |
| Talking clip | `She lifts [product] slightly toward the camera and says, "[one short line]". Small natural head movement, background stays still. Keep [text or product] unchanged.` |
| Start + end frame | `The [before] slowly transforms into [after]. Camera stays still. Keep the [label/logo] unchanged.` |

## Prompts as tested

| Prompt | Runs | Result |
| --- | --- | --- |
| The fries keep tumbling in a slow arc toward the open jar while a few potato slices drop back into the sack. Slow push-in toward the jar. Keep the jar label sharp and unchanged, background still. | 01, 03 | Usable on Seedance 2.0; Kling 3.0 ignored the push-in |
| A bright studio product shot of a ketchup jar with golden french fries and a burlap sack of potatoes on a wooden table, appetizing commercial food photography, vibrant colors, high quality, 4k. | 04 | Not usable: the model invented extra action |
| She slowly lowers her hand from her hair and turns her eyes to the camera, a faint smile forming. Hair settles naturally. Locked-off camera, soft studio light stays the same. Keep her face and the red sweater unchanged. | 02, 05 | Usable on both models; the camera still drifted on Seedance 2.0 |
| She slowly turns her head to the left over her shoulder, short hair catching the backlight. A few petals drift past in a light breeze. Camera holds still. Keep the flowers and the warm light unchanged. | 06, 07 | Correct on Seedance 2.0 Mini; Veo 3.1 Fast turned the wrong way. Use "screen left" so the side is never in question |
| She slowly turns her head toward screen left, looking back over her shoulder, short hair catching the backlight. A few petals drift past in a light breeze. Camera holds still. Keep the flowers and the warm light unchanged. | 15 | Right direction, but the photo drifted to anime style |
| She slowly turns her head and looks back over her shoulder, short hair catching the backlight. A few petals drift past in a light breeze. Camera holds still. Keep the flowers and the warm light unchanged. | 16 | Usable with an end frame facing screen left; no direction in the prompt |
| She lowers her hand and slowly turns her head toward screen left into a clean profile, then holds. Camera holds still. Keep her face, the red sweater and the dark background unchanged. | 17 | Usable; front-facing subject turned toward screen left (her right) |
| She lifts the box slightly toward the camera and says, "Six gummy-bear donuts, fresh this morning." Small natural head movement, cafe background stays still. Keep the menu board and the donuts unchanged. | 08, 09 | Exact speech on Seedance 2.0; extra words on MiniMax H3 |
| He pulls the can up and takes a quick sip, eyes still locked on the viewer. Hair flicks with the motion. Keep the loose pencil lines and flat colors, white paper background, no camera move. | 10, 11 | Not usable: style drift and an unwanted cut |
| Continuous single shot, no cuts. He pulls the can up and takes a quick sip, eyes still locked on the viewer. Hair flicks with the motion. Keep the goggles, the loose pencil lines and flat colors, white paper background, no camera move. | 14 | The cut was gone; the pencil texture still was not kept |
| The clear glass slowly transforms into cut crystal, facets catching the sunlight as the leaf shadows drift across the stone. Camera stays still. Keep the QUIETUDE label unchanged. | 12, 13 | Usable on both models (start + end frame) |

## Phrases that helped, and phrases that did not

- **Helped:** "Keep the [label / menu board] unchanged", "background still", naming a single action, "Continuous single shot, no cuts" (removed a hard cut once), "toward screen left" (read from the viewer's side in run 17), an end frame for the final pose (run 16).
- **Did not hold reliably:** "Locked-off camera", "Camera stays still", "no camera move", "slow push-in", "a few petals", "to the left".
- **Could not fix:** asking a model to keep loose pencil texture.

*Licensed under [CC BY 4.0](../LICENSE).*
