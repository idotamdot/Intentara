# GitHub Copilot Instructions for Intentara

## Project Overview

Intentara is a conceptual **Human Intention Map App** that visualizes human intention as a dynamic graph. This is currently a **design and architecture documentation repository**, not an active codebase.

**Vision**: "Map your lineage. Ignite your spark."

The app combines scientific measurement (Human Effect Index - HEI) with ceremonial design, creating a sanctuary where intention becomes visible, measurable, and meaningful.

## Core Concepts

### Human Effect Index (HEI)
- **Metrics**: Resonance, Persistence, Breadth, Velocity, Trust
- **Formula**: `E_a = w_r·R + w_p·P + w_b·B + w_v·V + w_t·T`
- **Decay**: `D(t) = e^(-λt)` - effects decay over time
- **Aggregate**: `HEI = Σ E_a · D(Δt_a)` - sum of decayed effects

### Presets (Creator Paths)
1. **Craft** - Measured creation, honored and remembered
   - Weights: R=0.25, P=0.30, B=0.20, V=0.10, T=0.15
   - Decay: λ=0.004/hour, Window: 28 days

2. **Community** - Connections weaving circles of resonance and trust
   - Weights: R=0.40, P=0.20, B=0.20, V=0.15, T=0.05
   - Decay: λ=0.008/hour, Window: 14 days

3. **Transmission** - Words carried, cited, and transformed
   - Weights: R=0.35, P=0.25, B=0.20, V=0.10, T=0.10
   - Decay: λ=0.006/hour, Window: 21 days

4. **Ritual** - Names and gestures invoked, adopted, and repeated
   - Weights: R=0.30, P=0.30, B=0.25, V=0.05, T=0.10
   - Decay: λ=0.005/hour, Window: 60 days

### Motifs
- **△ Triangles** - Three actions forming resonance loops
- **★ Stars** - Five actions radiating outward
- **◎ Hubs** - Central actions connecting many others

## Technical Architecture (Planned)

### Stack
- **Platform**: Android (Kotlin + Jetpack Compose)
- **Local Storage**: Room + SQLCipher
- **Privacy-First**: Local-only by default, optional sketch-only sync
- **Sketches**: Count-Min Sketch (CMS), HyperLogLog (HLL), Bloom filters
- **Graph**: Force-directed layout with ripple animations
- **Security**: Android Keystore, ed25519 signatures

### Data Models
```kotlin
enum class Preset { CRAFT, COMMUNITY, TRANSMISSION, RITUAL }
enum class Domain { CODE, COMMUNITY, CONTENT, RITUAL }

data class Action(
  val id: String,
  val timestamp: Long,
  val domain: Domain,
  val tags: List<String>,
  val resonance: Resonance,
  val persistenceDays: Int,
  val breadthContexts: Int,
  val velocityHours: Int,
  val trustScore: Double
)
```

## Coding Standards

### When Working on Implementation (Future)

1. **Kotlin Style**
   - Use data classes for models
   - Prefer sealed classes for type hierarchies
   - Use coroutines for async operations
   - Follow Kotlin coding conventions

2. **Compose UI**
   - Composables should be stateless when possible
   - Use `remember` and `mutableStateOf` appropriately
   - Follow Material Design 3 principles with custom theming
   - Animations should use `Animatable` and `LaunchedEffect`

3. **Privacy & Security**
   - Default to local-only storage
   - Encrypt sensitive data with SQLCipher
   - Use Android Keystore for key management
   - No telemetry without explicit opt-in
   - Transparent math - show all HEI calculations

4. **Testing**
   - Property tests for CMS/HLL/Bloom accuracy
   - Unit tests for HEI calculations
   - Fuzz tests for proof token verification
   - UI tests for Compose screens

## Documentation Standards

1. **Maintain the Vision**
   - Balance scientific precision with mythic language
   - Code comments should be minimal but meaningful
   - Documentation should explain "why" not just "what"

2. **Keep AGENT.md Updated**
   - AGENT.md is the living design document
   - Add new design decisions with rationale
   - Include formulas in LaTeX when relevant
   - Document data structures and schemas

3. **Narrative Language**
   - Use ceremonial language for user-facing text
   - Examples: "consecrate", "sanctuary", "lineage", "spark"
   - Balance expressiveness with clarity

## Design Principles

1. **Privacy-First**: Local computation, sketch-only summaries, proof-only sharing
2. **Transparency**: All formulas, weights, and calculations visible to users
3. **Anti-Gaming**: Caps, spike detection, rate limits
4. **Ceremonial UX**: Multi-sensory interactions (visual, haptic, sound)
5. **Creator-Focused**: Empower creators to see and tune their effect

## File Organization

- `/` - Root contains README.md and AGENT.md
- `/.github/` - GitHub configuration and instructions
- Future structure TBD as implementation begins

## Working with This Repository

### Current State
This is a **design document repository**. The AGENT.md file contains the complete architectural specification for the Intentara app.

### When Adding Features
1. First, document the design in AGENT.md
2. Include rationale and trade-offs
3. Specify data models and formulas
4. Consider privacy and anti-gaming implications
5. Describe UX flows with ceremonial language

### When Reviewing Changes
- Verify alignment with privacy-first principles
- Check that HEI formulas are mathematically sound
- Ensure ceremonial language maintains the sanctuary vision
- Confirm anti-gaming measures are in place

## Common Tasks

### Adding a New Preset
1. Define weights (must sum to ~1.0)
2. Choose decay lambda and window size
3. Set per-action and window caps
4. Create narrative templates
5. Document in AGENT.md with rationale

### Modifying HEI Calculations
1. Update formulas in AGENT.md with LaTeX
2. Justify the change mathematically
3. Consider impact on existing presets
4. Update caps if needed
5. Document expected behavior changes

### Designing UX Flows
1. Start with the narrative
2. Define visual, haptic, and sound cues
3. Create Compose implementation stubs
4. Document in AGENT.md
5. Consider accessibility

## Questions to Consider

When making changes, ask:
- Does this preserve user privacy?
- Is this transparent to the user?
- Can this be gamed? How do we prevent that?
- Does this align with the sanctuary vision?
- Is this mathematically sound?
- Will this work offline-first?

## Resources

- **AGENT.md**: Complete design specification
- **README.md**: Project overview and vision
- See AGENT.md for detailed formulas, data structures, and UX flows
