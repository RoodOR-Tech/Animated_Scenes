# Interactive Scene Design Pattern

Use this guide as the design brief for a new interactive scene. It captures the level of finish developed for Rood Hill Cemetery and applies it to places as different as a tidal pool, a working railway station, and an orbital greenhouse. The setting determines the mood, camera, materials, sounds, and pace.

## Start a new scene with one sentence

> Build **[place]** at **[time or condition]**. I want the visitor to feel **[mood]** and discover **[something worth staying to see]**. Use the attached Interactive Scene Design Pattern. Make reasonable choices for the remaining details and deliver a playable scene.

Example: “Build a Pacific Northwest ferry dock just before the first morning departure. I want the visitor to feel the quiet shift from waiting to work as the ferry eases into the slip.”

When interpreting the brief, decide where the visitor starts, what draws their eye, how they move, which object rewards close inspection, and what changes if they stay. Choose free exploration, a guided loop, a fixed viewpoint, or a combination that fits the request. For a Rood Hill–style browser experience, the reference pairing is free exploration and an unattended display loop.

## Build from the visitor’s viewpoint

| Build pass | What to decide or make | How to judge it |
| --- | --- | --- |
| 1. Space and scale | Block out the whole place, including the route beyond the first view. Set eye height or camera scale against a familiar object. Make thresholds, recesses, boundaries and elevation changes agree with the floor plan. | Walk, swim, fly or pan through the intended route with plain materials. Stop at the destination and look back. The space should still make sense. |
| 2. Composition | Hand-place the arrival view, a landmark that gives direction and a closer subject with room around its silhouette. Give the foreground, middle distance and background distinct shapes. | In a still frame, can a first-time visitor identify where they are and what deserves a closer look? In an open environment, a change of current, color or movement can supply direction. |
| 3. Objects and materials | Finish one object seen at close range before producing the rest. Model its outline and visible construction. Use texture and light for grain, roughness, residue and small surface marks. | Inspect it from across the space, three paces away and as close as the visitor can get. Each distance should reveal something different. |
| 4. Light and atmosphere | Establish the main light’s direction and softness. Add local lights where the scene gives them a source. Use atmospheric depth appropriate to the medium, such as suspended sediment, steam, dust or clear air. | Move past the object. Its shape should remain readable as highlights and shadows shift. Check that the brightest effect leaves important motion and lettering legible. |
| 5. Life and change | Choose what acts independently, what responds to the visitor and what persists afterward. A moving shadow, a machine completing a cycle or water draining from a rock can carry a scene by itself. | Stay still through one complete action. Look for its cause, the path it takes and the state it leaves behind. Check it again from the side. |
| 6. Sound and pacing | Establish a quiet background, a few placed sources, and an occasional foreground event. Decide which should dominate when two coincide. | Turn away from the source, change distance, then mute. Sound should locate or anticipate something. The visible action should still make sense in silence. |
| 7. Performance and delivery | Spend geometry and texture detail where the visitor can inspect it. Use simpler distant figures, repeated geometry and stable procedural scatter where appropriate. Preserve routes and key silhouettes at lower quality. | Try the actual packaged scene on the target display and input device. Record the device, renderer, observed performance and any untested path. |

## Give surfaces a reason to look the way they do

For each prominent object, answer four questions: What carries its weight? How is it joined? What touches it? Where do water, dust or light reach it? The answers tell you where to spend detail. A new installation may show precise seams, a protective film or a handprint. Age and damage are optional.

At Rood Hill, the entrance gate was convincing at a distance before it worked up close. Broad orange patches made the iron look painted. A charcoal finish, dull gray exposed edges, a slightly dropped gate leaf and a few bent pickets conveyed age more effectively. Moss gathered low on the masonry. The lantern supplied the warm color.

Apply the same inspection to a ferry bollard. From shore, its outline tells you where a line can catch. On the dock, the base flange and bolts show how it holds the load. Up close, a smooth band follows the path of wet rope. The sheltered underside keeps its rough finish. Those details describe a working dock even on a bright, dry day.

## Design one event for every way it can be seen

Write down the resting state, trigger, physical action, completion state and repeat rule. Use the same underlying action across modes. Give each mode its own way of presenting it.

| Decision | Worked example for the morning ferry |
| --- | --- |
| Resting state and source | The vessel is already visible beyond the pilings. Water moves against the empty slip. Its travel path continues into the space the visitor can see. |
| Free exploration | The approach can begin while the visitor faces another direction. An engine note announces it. The docking maneuver lasts long enough for someone to turn, and the ferry remains alongside afterward. |
| Guided display | Establish the empty slip. Turn toward the approaching bow before it reaches the pilings. Hold a dockside angle through contact with the fender so the vessel’s scale and weight register. |
| Physical consequence | The hull slows before contact, the fender compresses, the wake travels past the piles and subsides. Sound follows the position of the engine and the point of contact. |
| End and repeat | During a visit, the vessel stays docked until departure. For a looping display, reset during a view where the slip is out of sight, or stage a visible departure. Check a second loop for jumps and doubled audio. |

For a small, brief event, aim the guided camera before the event peaks. In free exploration, either wait for a suitable sightline, let the action linger, or leave a consequence to discover later. Choose what fits the subject. A scheduled train can arrive whether anyone is watching. A shy animal might wait for stillness before emerging.

## Reuse the scene architecture

Keep the world layout, actor state, camera choreography and rendering code identifiable. Choose new content for each production. These landmarks are useful if the builder has the Rood Hill HTML available.

| System | Rood Hill implementation | What carries forward |
| --- | --- | --- |
| Space | `buildWorld`, `ground`, `walkable`, `walkingFloor` | Use one spatial model for visible geometry, collision, routes and camera height. Hand-place landmarks, then seed background variation outside reserved sightlines and paths. |
| Materials and lighting | `surfaceCoordinates`, `moonMap`, `webgpu`, `webgl`, `software` | Give surfaces consistent texture scale and lighting. For fixed lighting, a baked shadow map can preserve depth economically. Check changed materials in each supported renderer. |
| Motion and navigation | `placeFigure`, `writeBirdPose`, `clearRoute`, `detour`, `tombPose` | Align art, pivots, contact points and travel paths. Check side and rear views of nearby subjects. Use obstacle-aware routing for autonomous movement and authored paths for precisely staged actions. |
| Direction and audio | `shots`, `cues`, `autoCamera`, `updateWalk`, `makeAudio`, `start`, `showMenu` | Keep world events separate from camera movement. Define which cues use elapsed time, proximity, gaze or visitor progress. Define what resets on replay, mute, mode change and return from a hidden tab. |

Rood Hill’s 55-second loop, 1.63-unit walking eye height and 2.65-unit-per-second walking speed are useful calibration points for a human-scale walk. For a tide pool, set the camera against a shell or blade of kelp. For an orbital greenhouse, use a tray, a hatch and the reach of a gloved hand. Choose pace by timing how long it takes to notice the scene’s smallest important action.

## Translate the pattern across settings

| Setting and mood | Detail to inspect | Change worth watching |
| --- | --- | --- |
| Tidal pool at low water, curious and quiet | A barnacle band marks the previous waterline. Exposed rock dries unevenly while sheltered crevices stay glossy. | A surge reaches a side channel. Fronds lift, bend with the current and settle as the pool drains. The visitor can watch from one place. |
| Railway workshop, busy and precise | A lathe has a rigid bed, polished handles and curled swarf below the cutting point. | The carriage advances along its guide. The pitch of the cut changes under load, the tool withdraws and the spindle coasts down. |
| Orbital greenhouse, calm and meticulously maintained | Transparent panels sit in gasketed frames. Condensation forms on the cooler pane, and tray latches show polished contact faces. | A grow-light bank comes on in sequence. Reflections move across the glass and the fan spins up. A fixed observation view can carry the entire cycle. |

## Review before calling the scene finished

- [ ] **Orientation.** A first-time viewer can identify a focal point in the opening frame. On a navigable route, check the destination, perimeter, return view and every change of floor height.
- [ ] **Close inspection.** Examine the nearest important object from the front, side and back. Move sideways along broad surfaces to expose flickering layers, gaps, stretching or floating geometry.
- [ ] **Material clarity.** View the same materials under two lighting conditions. Check that scale, texture direction, wear and reflections make physical sense.
- [ ] **Motion.** Watch the full action from a stationary viewpoint. Check origins, contacts, acceleration, occlusion and the final state. Turn away at the expected moment, then look back.
- [ ] **Modes and reset.** Re-enter, revisit an event and watch two loops wherever supported. Verify the camera, actors, lights and outstanding sounds start the next pass in the intended state.
- [ ] **Delivery.** Test the normal entry point, touch or keyboard controls as applicable, audio after user interaction, mute, reduced motion and the intended fallback. Check that the packaged assets load from the delivery location.
- [ ] **Evidence.** Keep an arrival frame, a near-material frame and the representative change in motion. Record the scene-specific decisions and any remaining limitations beside the playable build. These become the reference for the next scene.
