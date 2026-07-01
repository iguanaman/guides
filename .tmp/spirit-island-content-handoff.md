# Spirit Island Guide — Content Handoff (Core Strategy / Mechanics / Team Building / Tips)

Ready-to-paste HTML for four `<section>` bodies in `spirit-island/index.html`. Replace each section's placeholder `section-intro` + card-grid/accordion contents with the blocks below. Section wrapper tags (`<section id="...">`, `<h2>`) are unchanged — only the intro paragraph and inner markup are new.

---

## SECTION 1 — Core Strategy (`id="core-strategy"`)

```html
<p class="section-intro">Every spirit, every game, shares the same underlying puzzle before you specialize into a playstyle: read which win condition your table is actually racing toward, spend tempo on disrupting the invader pipeline rather than just mopping up after it, and know which resources are worth defending versus worth losing. The principles below apply regardless of which spirit is in front of you.</p>
<div class="card-grid">
  <div class="info-card">
    <h4>Fear Is a Win Condition, Not a Side Effect</h4>
    <p>Spirit Island has two parallel win paths: clear every Invader off the board, or advance the Fear track until a Fear card itself ends the game. New players default to board-clearing and treat Fear as flavor text, but the Fear track is usually the faster, more forgiving route — the board-clear requirement actually loosens as Terror Level rises (eventually you only need to clear cities and towns, not every last Explorer). A power that deals 2 damage and generates 2 Fear is often a better play than one that deals 4 damage and none. Check the Fear track's current tier before choosing your line for the round, and don't discount a card just because its damage number looks small.</p>
  </div>
  <div class="info-card">
    <h4>Disrupt the Pipeline, Don't Just React to It</h4>
    <p>Invaders run Explore → Build → Ravage every round whether or not you act. You cannot out-race that pipeline by only killing what's already on the board — a land you ignore this round explores again next round regardless. The efficient target is upstream: killing or moving an Explorer before it builds prevents both the Build and the Ravage that would have followed. Ask "what enters the pipeline this round" before asking "what do I kill," and prioritize actions that remove pieces before they escalate rather than punishing them after.</p>
  </div>
  <div class="info-card">
    <h4>Defense Before Offense, Every Round</h4>
    <p>Before playing any card, identify which lands will actually Ravage this round — that's the damage you cannot undo. Secure or accept those first; only then look for offensive or disruptive plays elsewhere. The common beginner failure mode is chasing satisfying Invader kills on turn 1 while a Ravage that was fully preventable goes unaddressed, because killing feels productive and defending doesn't. Triage by "what happens if I do nothing here this round," not by which play looks strongest on its own.</p>
  </div>
  <div class="info-card">
    <h4>Fast vs. Slow Power Timing</h4>
    <p>Fast powers resolve before the Invader phase and can stop this round's Ravage outright. Slow powers resolve after Invaders act, so they set up future rounds rather than saving the current one. Confusing the two — relying on a Slow power to save a land that Ravages this round — is one of the most common and most game-losing rules errors in the game. Before committing to a defensive plan, check whether the power you're counting on actually resolves in time; if not, you need a Fast answer or you need to accept the loss.</p>
  </div>
  <div class="info-card">
    <h4>Coastal Chokepoints Early</h4>
    <p>Invaders only ever enter the board via coastal lands. Spreading Presence evenly across the map wastes early tempo — concentrating on coastal lands in the first few rounds, before Towns fill those regions, chokes off inland spread for the rest of the game. This is front-loaded value: the same Presence placed on the coast in round 1 is worth far more than the same Presence placed inland in round 4, because it prevents an entire lineage of future Explore/Build/Ravage cycles rather than answering one.</p>
  </div>
  <div class="info-card">
    <h4>Fast Spirits, Slow Spirits, and Why Both Win</h4>
    <p>Some spirits (Lightning, Shadows) come online almost immediately and punch hard from round one; others (Earth, Keeper-types) are deliberately slow, spending early turns building a board-wide engine that pays off from the midgame on. Neither approach is strictly better — a fast spirit buys the table time for a slow spirit to ramp, and a slow spirit's eventual ceiling can outscale what a fast spirit sustains solo. The tempo mismatch is a feature: your team's plan should explicitly account for who is carrying which rounds, rather than expecting every spirit to contribute evenly turn over turn.</p>
  </div>
  <div class="info-card">
    <h4>Energy Is the Real Bottleneck, Not Card Count</h4>
    <p>Having a hand full of powerful cards is worthless if you can't afford to play them. Energy income (from your growth track and innate effects) determines how many of your options are actually live each round — track it as deliberately as you track board threats. When a growth choice trades presence/cards for energy, weigh it against whether you're currently option-constrained (too few plays) or energy-constrained (too few affordable plays); the correct growth pick differs depending on which bottleneck you're actually facing.</p>
  </div>
  <div class="info-card">
    <h4>"Always Thin the Biggest City" Is a Trap — Usually</h4>
    <p>Big Invader cities look like the highest-value target because they represent the most accumulated threat, but a card that clears a stacked city is often a card that could have prevented three separate smaller Ravages elsewhere for the same cost. Concentrated Invader stacks are dangerous precisely because they're expensive to deal with — piling more defense onto an already-big problem has diminishing returns compared to keeping smaller lands from ever reaching that size. The exception: when a city is about to trigger a cascading Blight chain, sits on a Fear-card condition you need, or is the one land standing between you and a Terror Level threshold — then it is the correct target. Default to prevention; escalate to demolition only when the math (Blight cascade, Fear timing, endgame clock) says so.</p>
  </div>
  <div class="info-card">
    <h4>Solo Play Demands Self-Sufficiency; Multiplayer Rewards Specialization</h4>
    <p>Solo, every gap in your spirit's toolkit is a gap nobody else covers — you must draft or grow around your own weaknesses. Multiplayer changes the underlying puzzle rather than just scaling it up: spirits that struggle to be self-sufficient (no reliable answer to some Invader type, slow cleanup) often perform much better with a partner, because you can informally trade tempo ("I clear this, you clear that") and lean on support cards that do nothing solo. Don't judge a spirit's multiplayer strength by imagining it trying to solo-cover the whole island — judge it on how well it handles its natural share and trades with the rest of the table.</p>
  </div>
  <div class="info-card">
    <h4>Let Difficulty Level Set Your Risk Tolerance</h4>
    <p>At low difficulty, the Ravage clock is slow enough that losing an undefended, Dahan-free, Blight-free land is a real, affordable choice — you'll get a recovery window later, so spend your tempo building your engine instead of firefighting everything. At high difficulty, that slack disappears: cascading Blight and faster Invader escalation punish the same "let it go" calls that were free at lower levels. Recalibrate how aggressively you cut losses (see the Mechanics section on Blight) based on the difficulty you're actually playing, not on a fixed rule of thumb from your last game.</p>
  </div>
  <div class="info-card">
    <h4>Expect an Early Struggle — That's the Shape of the Game</h4>
    <p>Games follow a predictable arc: Invaders are ahead for the first several rounds, there's a midgame inflection point, and spirits pull ahead from there as engines come online. Don't panic or overcommit resources trying to prevent early damage that isn't fatal — strategic patience early (accepting some Blight, some lost lands) is what lets your spirit reach the power spike that actually wins the game. Judge your position against the arc, not against a spotless board.</p>
  </div>
  <div class="info-card">
    <h4>Talk Before You Plan</h4>
    <p>Two minutes of table talk before each planning phase — which lands Ravage this round, what each spirit can actually do about it, and what's falling through the cracks — consistently outperforms silent parallel play. It feels slow, especially at higher player counts, but catches the coverage gaps and Fast/Slow mistakes that lose games. Coordinate in outcomes ("that mountain is handled"), not full inventories of your hand — you're aiming for shared situational awareness, not a play-by-play.</p>
  </div>
</div>
```

---

## SECTION 2 — Mechanics Deep-Dives (`id="mechanics"`, accordion)

```html
<p class="section-intro">These are the mechanics that reward a deeper read than their card text suggests — keywords and systems that cut across every spirit rather than belonging to any one of them. Understanding when they're strong, and when they're a trap, separates a mechanically-fluent table from one that's just moving pieces.</p>
<div class="accordion" id="mechanics-accordion">
  <div class="accordion-item">
    <div class="accordion-header"><span>Isolate — a scalpel, not a wall</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>Isolate (Jagged Earth) severs a land's adjacency for Explore, Build-related movement, and adjacency-dependent effects — it doesn't destroy anything, it just breaks the logistics link. Used once, speculatively, it's a minor add-on worth roughly a point of Fear or a bit more than Defend 1 — noticeably underwhelming, and new players who try it a couple of times often walk away unimpressed. It only becomes strong with volume or precision: spirits that can apply it repeatedly (Downpour Drenches the World repeating a land power, Finder of Paths Unseen's innate) or players who target it deliberately rather than guessing. <strong>Target Explorer sources, not destinations</strong> — isolating the land Invaders would explore <em>from</em> deterministically blocks Explore into every land adjacent to it, instead of gambling on which single destination gets explored. Isolate is also the answer to several adjacency-dependent Adversary rules (e.g. Scotland's coastal "trading port" adjacency, Russia's post-Ravage movement) — check whether an Adversary's special rule depends on adjacency before dismissing Isolate against it. It does not affect Dahan movement, spirit targeting, or Blight cascade — those all ignore Invader logistics entirely.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>Blight as a resource, not just a countdown</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>Treat presence, Dahan, energy, and Blight as fungible resources whose relative value shifts by situation, rather than a checklist you're obligated to keep clean. A single Blight token, an individual presence marker, or Dahan losses (as long as enough survive to retaliate) are usually acceptable losses — hindsight across many games shows players over-invest in defending every last point when that tempo would have won more games spent on growth or offense. The real danger isn't isolated Blight, it's <strong>cascades</strong>: a land can stack 3-4 Blight from repeated neighboring cascades, and once every land on the board is Blighted, any further Blight triggers a chain that is effectively the true loss condition — not the Blight counter itself. Intervene actively when a land faces multiple Invader actions in one cycle (Ravage-Build-Ravage compounds fast), when Blight is clustering adjacent to already-Blighted lands, or when an action would flip the Blight Card. Otherwise, let it ride.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>The Blight Card / Event Deck coupling</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>The Blight Card tracks Blight not yet on the island; its "Blighted Island" side has a pool size that acts as a hidden pacing dial — how much buffer exists between the island flipping and an outright loss. If you're running the Event Deck, a Blight Card is mandatory, since many Events reference island Blight state directly. If you're <em>not</em> running events, avoid thin Blight Cards (around 2 Blight/player on the blighted side) — those were balanced around the mitigation events provide, and without events they just make the post-flip phase brutally short with no compensating variety. Solo tightens this further: a thin card that's manageable when 2-4 players share the response burden becomes especially punishing when one player covers every leak alone. Choose your Blight Card based on which modules are in play and your player count, not as a fixed default.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>Reading the Fear deck — tiers and thresholds</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>The Fear deck is split into groups by Terror Level, with each Fear card printing multiple tiered effects — resolve the tier matching your <em>current</em> Terror Level, not the weakest top line. Using only the top effect once a stronger tier is unlocked is a common misplay that quietly costs a team real value every time a Fear card is drawn. Destroying towns and cities is one of the most reliable Fear generators, which is part of why "always kill the biggest stack" and "prioritize Fear" often point at the same targets even though they're different justifications — check which one actually applies before assuming they agree. Once a Fear win is realistically close, shift the whole team's priorities from territorial defense to maximizing Fear output; defending land you're about to win anyway is wasted tempo.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>Sacred sites as an investment, not a bonus</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>A sacred site is presence committed to a specific land to unlock a card's bonus effect there — it's a targeting requirement, not free upside, and it only pays off if you can actually deliver the matching power to that land on the turn(s) you need it. Placing a sacred site early to guarantee a strong Slow power lands cleanly later is a legitimate use of tempo, but only when you're confident that land will still be relevant (not overrun, not already cleared) when the payoff card comes due. Isolating a land that hosts a valuable sacred site is a solid way to guarantee it survives a Stage where you can't otherwise defend it.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>Elemental thresholds — a hidden co-op layer</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>Major powers typically carry an elemental threshold that unlocks a bonus effect if enough matching elements were generated that turn; minors usually don't. Elements come from the card itself, from growth choices, from innate/presence-track effects, and — depending on the specific card's wording — sometimes from teammates' plays too, which is a frequent source of table confusion (some thresholds check only your own elements, others check the whole board). Don't evaluate a major's "floor" effect in isolation: its real ceiling depends on what element support is available that turn, which is exactly why some cards function as deliberate co-op glue rather than solo-optimal picks. Treat element collection as a planned target when your spirit's innate or a held major needs a specific element, not something that happens incidentally.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>Play vs. Use vs. Threshold (and why the distinction matters)</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>Three distinct things happen with a card, and conflating them causes real rules errors: <strong>Play</strong> is paying the cost and placing the card into play; <strong>Use</strong> is actually resolving its effect in the Fast or Slow phase; <strong>threshold</strong> is meeting its elemental requirement, checked at end of the Spirit phase (or at play time, if played later). You can Play a card purely for its elements without ever intending to Use its effect. Less obviously, you can meet a threshold without ever Using the card at all — for example playing a Slow-phase card during the Spirit phase, having its threshold check succeed at end of Spirit phase, and then the game ending (win or loss) before the Slow phase would have resolved the effect. "Threshold met" and "effect used" are independent — don't assume one implies the other when tracking what a turn actually accomplished.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>Aspects and Incarna (Nature Incarnate) — mechanic-level primer</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p><strong>Aspects</strong> are alternate configurations of an existing spirit — they can swap out special rules or innate powers, change setup, add new unique power cards, or grant Incarna access, letting a table get a materially different playstyle out of a spirit they already own without learning an entirely new one. <strong>Incarna</strong> is a physical token representing the spirit's avatar directly on the board; it counts as presence for movement purposes and is available to several new Nature Incarnate spirits directly plus a handful of older spirits via their Aspects. Practically, an Aspect changes not just numbers but the shape of the decisions a spirit asks you to make each turn — read an Aspect's changed special rule/innate before assuming a spirit you already know will play the same way.</p></div>
  </div>
  <div class="accordion-item">
    <div class="accordion-header"><span>Digital client quirks (Steam app — not tabletop rules)</span><span class="chevron">&#9656;</span></div>
    <div class="accordion-body"><p>A handful of interactions are worth flagging specifically for the digital client. <strong>Isolate</strong>: for each nearby action, the app asks you (per action, per instance) whether the isolated land counts as connected — it isn't a fixed one-time toggle. <strong>Tokens that can count as multiple things</strong> (e.g. a Many Minds Move as One sacred site counting as an animal, or a Settle Into Hunting-Grounds token counting as both animal and badlands): the app lets you decide per-token, per-action, which matters when an Event or Adversary effect targets/removes "animals" — opt individual tokens out to protect them. <strong>Sacrifice victories</strong>: an action resolves fully before win/loss is checked, so if a single action simultaneously satisfies a win condition and triggers a loss condition (e.g. runs the Blight pool dry), the app rules it a win. These are implementation clarifications, not tabletop house rules — worth knowing if you play both formats so you don't misapply one ruleset to the other.</p></div>
  </div>
</div>
```

---

## SECTION 3 — Team Building (`id="team-building"`)

```html
<p class="section-intro">Multiplayer Spirit Island isn't solo play with extra hands — assembling a table of spirits is a distinct puzzle, since each spirit's toolkit is deliberately incomplete and depends on the group to cover what it can't. A good lineup trades weaknesses for strengths rather than stacking redundant ones.</p>

<h3>Pairing Principles</h3>
<div class="card-grid">
  <div class="info-card">
    <h4>Cover the Gap, Don't Duplicate the Strength</h4>
    <p>Every spirit is missing something by design — a reliable answer to some Invader type, a way to clean up what it starts, raw damage, or range. The strongest tables aren't the ones stacking multiple spirits that are all great at the same thing; they're the ones where each spirit's blind spot is another spirit's specialty. A spirit that's mediocre solo specifically because it lacks self-sufficient cleanup (relies on someone else to finish what it starts) is often excellent multiplayer paired with a spirit that has exactly that cleanup tool.</p>
  </div>
  <div class="info-card">
    <h4>Pair Fast Tempo with Slow Ceiling</h4>
    <p>A fast-acting spirit (immediate board impact from round one) buys time for a slow-building spirit (weak early, dominant once its engine turns on) to ramp without the table losing control in the meantime. Two fast spirits can both flame out once Invaders scale past their ceiling; two slow spirits can both get run over before either comes online. Explicitly pairing tempo profiles — not just raw power level — smooths the table's power curve across the whole game instead of concentrating both weak points (early and late) at once.</p>
  </div>
  <div class="info-card">
    <h4>Trade Tempo Informally, Turn to Turn</h4>
    <p>Multiplayer's real advantage over solo isn't just more hands — it's the ability to informally barter resources across turns: "I take an extra Presence placement and clear your Explorers next round." This lets a spirit lean on a partner's strength instead of needing to be self-sufficient, and it's the main reason spirits that look weak solo often perform fine at the table. Build this into your team's shorthand explicitly rather than assuming it happens automatically — a round of "who can cover what" during planning is where these trades actually get made.</p>
  </div>
  <div class="info-card">
    <h4>Read the Adversary Before Finalizing the Lineup</h4>
    <p>An Adversary's specific triggers matter more than its raw difficulty number — a spirit that struggles with an Adversary's core engine (e.g. a spirit with no ranged answer against an Adversary that punishes coastal buildup) is a worse pick than the numbers alone suggest, and vice versa. Where the table can see the Adversary before assigning spirits, lean the lineup toward whichever spirits directly answer that Adversary's pressure points (fast removal against a rapid builder, Fear-generation tools against one with a brutal late Blight curve) rather than picking spirits in a vacuum.</p>
  </div>
  <div class="info-card">
    <h4>Coordination Overhead Scales Faster Than Player Count</h4>
    <p>Two-spirit tables can coordinate with a quick "I've got the coast" exchange; four-to-six-spirit tables need actual shorthand or planning grinds to a halt. Set shared priorities as simple rules ("fast powers on the mountain lands, slow on wetlands") and communicate in outcomes ("that region's handled") rather than listing which cards you're using — the goal is shared situational awareness, not a full inventory of every hand. At high player counts, resist the urge to compute every other spirit's optimal line for them; state your own capabilities and gaps at a high level and trust the group process, since nobody has full visibility into another player's hand and board state anyway.</p>
  </div>
</div>

<h3>Notable Combos</h3>
<div class="card-grid">
  <div class="info-card">
    <h4>Blight-Soak + Free-Swinging Damage</h4>
    <p>Pairing an aggressive, damage-forward spirit with one built to absorb or relocate Blight (pulling it onto its own cards/land rather than letting it hit the shared island pool) lets the aggressive spirit play without the team eating its Blight downside. This is a direct application of the "cover the gap" principle: one spirit's cost becomes the other spirit's specialty.</p>
  </div>
  <div class="info-card">
    <h4>Relocation Feeding a Kill Zone</h4>
    <p>A spirit that can teleport or forcibly relocate Invaders can move problem targets (e.g. inland cities) into a zone another spirit reliably dominates (e.g. a coastal-kill spirit that's normally limited to the shoreline). This pattern generalizes: any spirit with strong movement/displacement tools is a force-multiplier for any spirit with a strong but narrow kill zone, since it extends that zone's effective reach across the whole board.</p>
  </div>
  <div class="info-card">
    <h4>Generator + Payoff (Beast/Token Economies)</h4>
    <p>Some spirits flood the board with a resource (beast tokens, Dahan, strife/disease markers) without much of a payoff themselves, while other spirits convert that same resource into damage or control. Pairing a generator with its natural payoff spirit turns two individually-middling engines into a strong one — check whether a spirit's stated weakness ("I make a lot of X but can't use it") is answered by another spirit's stated strength ("I convert X into Y") before assuming the pairing is arbitrary.</p>
  </div>
  <div class="info-card">
    <h4>Ramp Spirits Feeding a Slow, High-Ceiling Third</h4>
    <p>In three-plus spirit games, it's worth dedicating one or two spirits to accelerating a slow-but-high-ceiling teammate's presence/energy growth rather than insisting every spirit pull independent weight from turn one. A slow spirit that would normally take many rounds to come online can hit its power spike far earlier if teammates spend early tempo feeding its ramp instead of racing to contribute damage themselves.</p>
  </div>
  <div class="info-card">
    <h4>The Pipeline Combo: Push, Kill, Control</h4>
    <p>A three-spirit shape that recurs across many strong lineups: one spirit pushes/funnels Invaders toward a chokepoint, a second spirit provides the reliable kill at that chokepoint, and a third adds Fear or board-wide control to manage whatever slips through. This is a repeatable, low-variance pattern rather than a specific named combo — the underlying principle (funnel → finish → clean up) can be built from many different spirit combinations, not just one canonical trio.</p>
  </div>
  <div class="info-card">
    <h4>Treat "Best Pairing" Polls with Caution</h4>
    <p>Crowd-sourced "best pairing" rankings often measure thematic appeal or table-favorite status as much as actual synergy — a top-voted pair can turn out to be "fine, but nothing special outside of matching flavor" once actually played. Use community pairing suggestions as leads to try, not as proven optimal-play combos; verify a suggested pairing's synergy against what the two kits actually cover for each other, not against its popularity.</p>
  </div>
</div>
```

---

## SECTION 4 — Tips & Tricks (`id="tips"`)

```html
<p class="section-intro">Smaller-grain lessons that don't rise to core strategy but repeatedly trip up new tables — misplays, sequencing tricks, and a few digital-client-specific gotchas worth knowing before they cost you a game.</p>
<div class="card-grid">
  <div class="info-card">
    <h4>Learn the Base Game Before Adding Modules</h4>
    <p>First games should skip Blight Cards, Adversaries, and Special Scenarios entirely — get comfortable with the core Explore/Build/Ravage loop and your spirit's own kit before layering on modules that change the math. Adding difficulty before the fundamentals are solid usually just produces a loss nobody can diagnose, since it's unclear whether the module or a basic misplay caused it.</p>
  </div>
  <div class="info-card">
    <h4>Don't Skip Your Spirit's Special Rule</h4>
    <p>Every spirit has a unique special rule beyond its power cards, and new players routinely forget to use it or don't realize it's central to how the spirit is meant to function. Read it as carefully as the starting powers — for several spirits, the special rule (not any single card) is the actual engine the rest of the kit is built around.</p>
  </div>
  <div class="info-card">
    <h4>Move Invaders, Don't Just Kill Them</h4>
    <p>Push/pull effects look weak next to direct-damage cards but are frequently the more efficient play: they can hit more Invaders per card than a damage effect, get threatened Dahan out of harm's way, and — critically — can prevent a Build or Ravage before it happens rather than punishing it after. Don't undervalue a control card just because its damage line reads as zero.</p>
  </div>
  <div class="info-card">
    <h4>Stack Dahan Instead of Spreading Them</h4>
    <p>Dahan defense is a threshold effect, not a linear one. Two Dahan against a lone Explorer can end in a wash (the Explorer's town survives the counterattack); three Dahan in the same spot can wipe the Explorer outright. Concentrating Dahan into fewer, thicker stacks — especially on the periphery where your card plays can't reach in time — beats spreading them thin, since a stack below the threshold contributes far less than its number suggests.</p>
  </div>
  <div class="info-card">
    <h4>Never Discard Your Starting Power Cards</h4>
    <p>Starting powers are deliberately elemental-diverse — that diversity is often exactly what an innate power's threshold depends on. When upgrading to major powers, replace cards you picked up mid-game, not your original starting hand; discarding a starting power can quietly break an innate you were relying on without it being obvious until the elements don't add up.</p>
  </div>
  <div class="info-card">
    <h4>Pick Cards for Elements When You're Threshold-Constrained</h4>
    <p>When you're close to unlocking an innate's elemental requirement, take the card that supplies the missing element over the card with the flashier effect — closing the gap can save an entire extra card play that turn, which means less presence spent and a faster reclaim cycle. This isn't a universal rule; it only applies once you're actually near a threshold. Earlier in the game, with more slack, pick for effect quality as normal.</p>
  </div>
  <div class="info-card">
    <h4>Know Which Lands Are Cheap to Lose</h4>
    <p>An undefended land with no Dahan and no Blight yet is a safe sacrifice — the cost of defending it usually exceeds its value, especially early or at lower difficulty where there's a recovery window. Learn to distinguish "cheap to lose" lands from lands that are expensive to lose (Dahan present, Blight already clustering, sacred site committed) so that letting something go is a deliberate read, not an accident.</p>
  </div>
  <div class="info-card">
    <h4>Physically Track Your Spent Resources</h4>
    <p>Place energy tokens directly on growth-track options as you gain them, place tokens on cards as you commit to playing them, and tap/exhaust cards as you activate them rather than doing it from memory. None of this changes strategy, but per-turn state in this game is dense enough that "which of my numbers is already spent" errors are one of the most common sources of accidental misplays, especially for new players.</p>
  </div>
  <div class="info-card">
    <h4>Digital Client: Per-Instance Choices Aren't One-Time Toggles</h4>
    <p><em>Digital (Steam app) only.</em> Some interactions ask you to decide per-action rather than setting a fixed state once — e.g. whether an Isolated land counts as connected for a given action, or whether a token that can count as multiple things (an animal and badlands, for instance) counts as one or the other for a specific effect. New players sometimes assume these are set-and-forget toggles; check the prompt each time it appears, since choosing wrong on one instance doesn't lock in the same choice for the next.</p>
  </div>
  <div class="info-card">
    <h4>A Card Can Meet Its Threshold Without Ever Resolving</h4>
    <p>Elemental thresholds are checked at end of the Spirit phase, independent of whether the card's effect ever actually resolves in the Fast/Slow phase that follows. It's possible to play a Slow-phase card purely for its elements, hit the threshold, and then have the game end (win or loss) before the card's own effect would have triggered. Don't assume "threshold met" means "effect happened" when reviewing what a turn accomplished — they're tracked independently.</p>
  </div>
</div>
```
