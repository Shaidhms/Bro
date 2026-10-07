# New Bro characters: prompt pack

Same workflow as the denim Bro:

1. Make the **base image** in ChatGPT.
2. Make each **clip** in Kling image-to-video, using that image as the start frame.
3. Import the files into Bro.

Add this to the end of every clip prompt:

> Static camera, plain white background, full body visible the whole time (head to feet), no zoom, no camera movement. Same character, same design, 3D Pixar-style animation.

Negative prompt for every clip:

> camera movement, zoom, cropped feet, cut off head, background objects, extra limbs, extra fingers, distorted face, blurry, text, watermark, logo

Settings for every clip: 5 seconds, 3:4 or 9:16, Professional / High quality.

---

## 1. Captain Hydro (original superhero)

### Base image → `idle.png`

> 3D Pixar-style animated superhero character, an original design (not based on any existing hero): a friendly, confident young Indian man with short spiky black hair and a warm smile. Sleek blue and aqua superhero suit with a silver water-drop emblem on the chest, short flowing aqua cape, silver boots and gloves, a slim blue domino mask. Standing facing the camera, hands on hips in a proud hero pose. Full body visible including boots. Plain solid white background, soft studio lighting.

### Clips

| File | Prompt (then add the line from the top of this page) |
|---|---|
| `walk.mp4` | The hero turns to the side and walks in place facing right, a confident heroic walk cycle, cape gently swaying, arms swinging. He stays on the same spot, like on a treadmill. |
| `run.mp4` | The hero turns to the side and runs in place facing right: a fast superhero sprint, body leaning forward, fists pumping, cape flying behind him. He stays on the same spot. |
| `water.mp4` | The hero pulls a clear water bottle from his belt, holds it out toward the camera with a big encouraging smile and a thumbs up with the other hand, as if saying "hydrate, citizen!", then holds that pose. |
| `warn.mp4` (sad) | The hero's smile fades, his shoulders drop, his cape droops, he shakes his head slowly in disappointment, then looks at the camera with sad eyes and holds the pose. |
| `angry.mp4` | The hero frowns, crosses his arms, his chest emblem glows bright aqua, then he points firmly at the camera with a stern "close it now!" look and holds the pose. Playful, not scary. |
| `happy.mp4` | The hero laughs and punches one fist up into the air in celebration, cape fluttering, then settles back into his hands-on-hips pose. |
| `hello2.mp4` (swag) | The hero gives a crisp two-finger salute from his brow toward the camera with a cheeky grin, flicks his cape over his shoulder, then returns to his hands-on-hips pose. |

Import (his walk faces right; check which way the run faces before importing):

```bash
cd ~/Documents/Shaid_Works/Nisha/desktop-buddy
TITLE="Captain Hydro" FPS=24 ./import-character.sh hydro ~/Downloads/hydro-poses
```

---

## 2. Biscuit the cat

### Base image → `idle.png`

> 3D Pixar-style animated cartoon cat, an original character: a chubby, fluffy orange tabby cat with big expressive green eyes, a tiny pink nose, white paws and chest, and a small blue denim bandana around the neck. Sitting upright facing the camera with a cheeky, happy expression, tail curled around the front paws. Full body visible. Plain solid white background, soft studio lighting.

### Clips

| File | Prompt (then add the line from the top of this page) |
|---|---|
| `walk.mp4` | The cat stands up and walks in place on four legs, side view facing right, a natural relaxed cat walk with the tail up and swaying gently. It stays on the same spot, like on a treadmill. |
| `run.mp4` | The cat runs in place, side view facing right: a playful bounding cat gallop, ears back, tail streaming behind. It stays on the same spot. |
| `water.mp4` | The cat pushes a small blue bowl of water toward the camera with one paw, looks up with big encouraging eyes, gives a little "meow", then sits holding the pose. |
| `warn.mp4` (sad) | The cat's ears droop flat, it lowers its head, its whiskers sag, then it looks up at the camera with huge sad pleading eyes and holds the pose. |
| `angry.mp4` | The cat arches its back, its fur puffs up, it swishes its tail and gives a dramatic cartoon hiss toward the camera, then sits glaring with narrowed eyes. Cute and funny, not scary. |
| `happy.mp4` | The cat purrs happily, does a little hop, and rolls onto its back with its paws in the air, then sits back up smiling. |
| `hello2.mp4` (swag) | The cat sits up, lifts one front paw and waves it at the camera, then smugly licks the paw and smooths its ear, then sits proudly. |

Import (both clips face right per the prompts):

```bash
cd ~/Documents/Shaid_Works/Nisha/desktop-buddy
TITLE="Biscuit the Cat" FPS=24 ./import-character.sh biscuit ~/Downloads/biscuit-poses
```

---

## After importing

- To switch character, right-click Bro → **Character**, or use **Settings → Character**.
- To bundle the characters in the shareable app:
  ```bash
  CHARS="denim hydro biscuit" ./build-share.sh
  ```
- **If a walk or run faces the wrong way,** edit `character.json` in the character's folder and set `walkFacesRight` / `runFacesRight` to `false`. Or send me the clips and I'll check them, trim the loops and import them.

---

## Spider-Man and Iron Man

If ChatGPT or Kling refuses a name, use the "backup" description.

### 3. Spider-Man → folder `spidey`

Base image → `idle.png`:

> 3D Pixar-style chibi Spider-Man figure, classic red and blue suit with black web lines and a black spider emblem, big white eye lenses, standing facing the camera in a playful pose, one hand doing the web-shooter gesture (middle and ring fingers down). Full body visible. Plain solid white background, soft studio lighting.

Backup description: "a friendly cartoon wall-crawling hero in a red and blue web-patterned suit with large white eye lenses".

| File | Prompt |
|---|---|
| `walk.mp4` | He turns sideways and walks in place facing right with a bouncy, acrobatic step, arms swinging loosely. Stays on the same spot. |
| `run.mp4` | He sprints in place facing right, low and agile, arms pumping like a parkour runner. Stays on the same spot. |
| `water.mp4` | He shoots a thin web line off-screen, yanks a clear water bottle into his hand, then holds it out toward the camera with an encouraging thumbs up, and holds the pose. |
| `warn.mp4` (sad) | He droops his shoulders, hangs his head, rubs the back of his mask awkwardly, then looks at the camera with drooping eye lenses and holds. |
| `angry.mp4` | He puts his hands on his hips, his eye lenses narrow, he taps his foot, then points firmly at the camera. Playful, not scary. |
| `happy.mp4` | He does a quick backflip on the spot, lands in a crouch, then pops up and gives two thumbs up. |
| `hello2.mp4` (swag) | He waves, then does his signature web-shooter hand gesture toward the camera with a cocky head tilt, and holds. |

```bash
TITLE="Spidey" FPS=24 ./import-character.sh spidey ~/Downloads/spidey-poses
```

### 4. Iron Man → folder `ironman`

Base image → `idle.png`:

> 3D Pixar-style chibi Iron Man figure, red and gold armor with a glowing blue arc reactor in the chest and glowing white eye slits on the faceplate, standing facing the camera with a confident stance, one fist on his hip. Full body visible. Plain solid white background, soft studio lighting.

Backup description: "a friendly cartoon armored hero in sleek red and gold armor with a glowing blue chest light".

| File | Prompt |
|---|---|
| `walk.mp4` | He turns sideways and walks in place facing right with a heavy, confident armored stride. Stays on the same spot. |
| `run.mp4` | He runs in place facing right in his armor, small bursts of blue thruster glow from his boots on each step. Stays on the same spot. |
| `water.mp4` | His palm panel opens with a blue glow and a clear water bottle slides out into his hand, then he holds it toward the camera with a nod, and holds the pose. |
| `warn.mp4` (sad) | His faceplate dims, his shoulders slump with a mechanical sigh, he shakes his head slowly, then looks at the camera and holds. |
| `angry.mp4` | He raises one palm toward the camera as his repulsor glows bright blue (no blast), eye slits narrowing, and holds the pose. Playful, not scary. |
| `happy.mp4` | He does a short hover hop with boot thrusters glowing, lands, and pumps a fist. |
| `hello2.mp4` (swag) | His faceplate flips up to show a smug grin, he gives a two-finger salute, then the faceplate snaps back down and he holds a confident pose. |

```bash
TITLE="Iron Man" FPS=24 ./import-character.sh ironman ~/Downloads/ironman-poses
```
