# Script for Cryptophysics talk

## Slide 1 - UTC

Black screen, white text, running clock

## Slide 2 - UTC w/ text

Black screen, white text, "this clock lies to you."

## Slide 3 - Genesis Time

Black screen, white text, running clock

## Slide 4 - Genesis Time w/ text

Black screen, white text, "This is the most honest clock there is."

(( FADE TO WHITE ))

## Slide 5 - Append

(( MUSIC STARTS SOFTLY ))

White screen, black text "Append. Nothing Else Matters."

(( FADE TO BLACK ))

## Slide 6 - Lattice Pic

(( FADE IN TO THE LATTICE ))

V/O: "It doesn't take much to change the world. Just got to hate date math enough to come up with a new clock that is elegantly mathematical. The philosophy we're talking about is called Trust Architecture. It's a new way to look at data structures by making time a core component of the record itself. Each of these structures—these luminous hexagons—represents an R⬢, a Record Hex. It’s not a file. It’s an event crystallized in spacetime: who acted, what they did, when they did it, and under which scope of meaning. Each one contains its own proof of existence. Together, they tessellate into the lattice—an informational crystal that never forgets." 

(( SHOW CLOCK AND DATA MERGING? IDK ))

## Slide 7 - GT clock over lattice

V/O: "To add time though, we have to have an absolute version of time, one that is calculated, not assigned by committee or king. We must correlate our data to a clock that operates outside of jurisdiction, one that operates based on the universe itself. A sidereal day is measured as the complete rotation of the planet relative to the stars. This day is then divided into 1,000 fragments, known as Marks. These marks can then further divided by 1,000 or 1,000,000, to create submarks and Micromarks. This makes up what we call Genesis Time or GT. It operates based on the universe itself. It can't be changed by the UN, a president, or the bank."

## Slide 8 - Fields flying in

V/O: "Once we have the clock, we need the intent. The author casts their intent in the form of 7 fields. 

- previous_hash: The BLAKE3 hash of its predecessor.
- scope: Namespace of the record to be appended.
- nonce: Unique ID generated to prevent replay
- author_pk: Author's public key
- usher_pk: Usher's public key
- record_type: What kind of record this is
- data: Dynamic storage for flexible data types

(( ZOOM OUT ))

This is the molecular structure of a truth event. Seven fields, each immutable once cast, bound together by a cryptographic signature. A single R⬢ is about 1.5 kilobytes—smaller than a tweet, yet heavy enough to anchor truth for eternity."

(( CROSS CUT ))
## Slide 9 - Show the data being signed

V/O: "Each record is submitted to an 'usher' for validation and temporal attestation. If the intent passes, the usher stamps it with the context, which consists of the current Genesis Time, and optionally spacial coordinates. The usher then signs over the author's signature and the context, performing the first transparent, verifiable attestation to the record. Think of the usher as a notary crossed with an atomic clock. They don’t judge the message; they confirm it existed, right then. That’s all truth needs—timing and witness."

## Slide 10 - Show a bunch of computers in a circle

V/O: "Sometimes an author's and usher's signatures are enough. Other times, we want to keep everyone honest, so we introduce quorum. Members of the scope's quorums can sign off on an author/usher signature pair as further attestations to the validity of the time. When multiple ushers sign the same R⬢, you get redundancy—not for trust, but for resilience. The lattice doesn’t care about belief; it cares about evidence density.”

## Slide 11 - Current Hash animation

V/O: "Finally, we calculate a hash over the whole package - intent, context, and signatures. This is the hash referenced by the next record's previous_hash. It is through those cryptographic links that we make a continuous chain of records, each chain labeled by their scope name. When that final hash is calculated, the R⬢ clicks into place like a facet on a gem. The next record will polish its neighbor, and so on, until the whole lattice glows"

(( FADE TO WHITE ))

## Slide 12 -  Lattice-Fu #2

White screen, black text "One structure, infinite worlds."

(( SUBTEXT FADES IN ))

Every scope—whether a business, a government, or a single human—is its own universe stitched into the same spacetime fabric. Scopes don’t compete; they resonate.

(( FADE TO BLACK ))

## Slide 13 - Joe's Diner exterior

V/O: "This is Joe's Diner. Joe has the freshest food in town, but he wants a way to prove it to his guests. Here's how the lattice can help Joe."

## Slide 14 - Tomato farm

V/O: "We start at the source. The McKenzies have been growing tomatoes in Joe's community for years. The McKenzies SelfID scope casts a R⬢ attestation for the harvest, which is then cross-signed by the USDA's regulatory scope. The tomatoes are now cryptographically bound."

(( SHOW TOMATO WITH COMICALLY HUGE QR ))

## Slide 15 - Transport Truck

V/O: "Acme Produce then collects the tomatoes from the McKenzies as an action on the lattice. Each hour in transit is recorded with verified temperature."

## Slide 16 - Delivery Guy bring in tomatoes

V/O: "Now we have the tomatoes arriving at Joe's. Now all Joe has to do is scan the manifest, and now has COMPLETE knowledge of the produce he's buying, including if it was handled correctly."

## Slide 17 - Show menu with QR code

V/O: "Guests can view when the produce arrived, that it was kept in a controlled environment, and that it was harvested in compliance with organic practices. Guests aren't guessing. They know, because the truth is cheap and accessible in the lattice. What happens when you can start verifying where all your food came from?"

## Slide 18 - Lattice-Fu

(( FADE TO WHITE ))

White screen, black text "Identity flows from keys; trust flows from attestations."

(( FADE TO BLACK ))

## Slide 19 - Joe talking to someone

V/O: "Imagine again you are Joe. You not only have the best food but the best place to work. You want to hire the most competent line cooks you can, but how can you do so in an industry that is known for restaurants going out of business? How do you verify someone when their history is a volatile as the kitchen?"

## Slide 20 - Person with floating attestations

V/O: With the lattice, you can create a SelfID, a portable data scope designed just for you. It allows you to collect attestations from employers and coworkers confirming either your employment or skills. The attestations are tied to _YOUR_ data you control. Joe doesn't trust a resume; he trusts a cryptographically verifiable trust graph. Cryptographically stored in your SelfID scope, Joe can scan these attestations instantly, without calling anyone or even if the place is out of business."

## Slide 21 - Show a crew, all holding up "votes"

V/O: "But this doesn't just hold true for the employee. Employees can attest anonymously to working conditions without using an Ephemeral Sub-ID. Joe is held accountable not by a newspaper, but by the immutable, time-anchored evidence of his own employees' actions. This keeps Joe honest with his employees about labor rates, working conditions, and benefits. Now not only can Joe show he has the freshest food, he can prove he treats his employees the best."

## Slide 22 - Show Joe, crossed arms

V/O: "So now the guests know how Joe runs his business, potentially before ever making the decision to eat there. Informed guests aren't just guessing that the wagyu is locally sourced, they know for certain. But how else can the lattice work for Joe?"

## Slide 23 - Lattice-Fu

(( FADE TO WHITE ))

White screen, black text: "Time is the substrate. Everything else is scaffolding."

(( FADE TO BLACK ))

## Slide 24 - The POS register

V/O: "That's right, the lattice comes into play even here, at the register. Something as simple as paying for food still has its fingerprints in the lattice."


## Slide 25 - Show the Register Screen

V/O: "Joe's register knows about the cryptographically bound tomatoes and has already figured it into his food costs, can show cost over time, and provides providence. But what else can we do with the lattice here?"

## Slide 26 - Show the cash drawer empty

V/O: "What if I told you the lattice not only can be used to calculate costs, but collect payment too. VeroCoin is a lattice native payment system, built into the rails, that can be used for reward points at Joe's Diner. Joe gets to offer a reward program without giving up his already narrow margins."

## Slide 27 - Show people in line

V/O: "The VeroCoin payment becomes not a transaction against the card networks, but a cast lattice record. This record instead of imposing a 2-3% fee only charges a modest 0.5%. Where does the fee go?"

## Slide 28 - World Map

V/O: "This modest fee funds the Universal Basic Income Trust, set up by the Trust Architecture Foundation. This is how the first world offsets the most destitute. The money collected is not hoarded; it is transparently redistributed to support the fundamental dignity of all SelfIDs."

## Slide 29 - Show a person at the register

V/O: "And since VeroCoin is just a lattice R⬢ tied to your SelfID, payment becomes not a transaction, but a handshake. The register shows the total as a QR code with a challenge, the AR glasses or phone scan, and the UI shows a simple "Pay/Decline". Once confirmed, the client just submits the R⬢ payment to Joe's wallet. No waiting on gateways, or payment processors. No T+2 resolution. Atomic settlement."

## Slide 30 - Lattice-Fu

(( FADE TO WHITE ))

White screen, black text: "A single R⬢ can move mountains."

(( FADE TO BLACK ))

## Slide 31 - Video, me in front of a green screen

Me: "What you've just witnessed is a day in the life of the lattice. This is what one industry looks like when onboarded to the lattice. We have already begun using this in industry."

## Slide 32 - Electric Motor

V/O: "Industrial electric motors are a thing no one thinks about but is critical to the world. We can track, monitor, and certify motors in real time, permanently. Each motor becomes its own R⬢ emitter. Certifications, service events, and failures become traceable physics. Maintenance stops being reactive—it becomes temporal cartography. But also, we can expand the lattice into almost any industry"

## Slide 33 - Show someone at a desk w/ graph overlayed

V/O: "The ledger stops being a book of debts and becomes a living map of value flows. Fraud evaporates under permanent daylight. “Auditing” turns into continuous physics—every transaction self-proves". A bank ledger that can’t be rewritten means corruption turns into noise instead of narrative. Accounting becomes observational physics: nothing hides, everything balances.

## Slide 34 - Show a doctor and patient

V/O: "Medical data becomes a self-governing ecosystem. Patients own immutable copies of their own histories, while doctors contribute verifiable treatments instead of notes lost in bureaucracy. Every prescription, every diagnosis, timestamped and attested. No vendor lock-in, no lost charts. The body becomes a verifiable dataset you actually own."

## Slide 35 - Show a journalist and a cameraman

V/O: "Every quote, photo, and clip carries a proof-of-origin. The attention economy inverts: credibility, not outrage, becomes the scarce commodity. Journalism anchored in R⬢ provenance breaks the arms race of misinformation. Proof-of-origin replaces proof-of-outrage."

## Slide 36 - Video, me, green screen

Me: "The power of the lattice feels near infinite, because it is. Infinitely parallel, the lattice can expand as big as it needs. Each scope its own digital sovereignty, with its own rules and authorities."

## Slide 37 - Close up, me, green screen

Me: "This is a new concept in how trust is measured and stored, and it was built for you. The tools are open source, and free to use. Build with them, cast your own records, and see a world of permanence we never thought possible. Because someday, every R⬢ you cast becomes a star in the same sky. And when people look back at this era, they’ll see exactly when we stopped deleting history and started remembering on purpose."

(( FADE TO BLACK ))

## Slide 38 - Credits
