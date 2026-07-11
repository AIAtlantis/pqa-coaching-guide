import React, { useState, useMemo } from "react";

/* ============================================================
   PRECISION Q+A — Interactive Coaching Guide
   Anchored to: Precision Questioning & Answering (PQ+A)
   Dennis Matthies & Monica Worline — Stanford CTL → Vervago
   Built for coaching sessions: explore, drill, practice.
   ============================================================ */

const T = {
  bg: "#ECEEF2",
  panel: "#FFFFFF",
  ink: "#15181E",
  inkSoft: "#4A5160",
  line: "#D6DAE2",
  cobalt: "#2247E6",
  cobaltSoft: "#E8EDFF",
  amber: "#B5720F",
  amberSoft: "#FBF1DE",
  green: "#1D7A4A",
  red: "#B3362C",
};

const FONT_LINK = `
@import url('https://fonts.googleapis.com/css2?family=Archivo:wdth,wght@62..125,400..900&family=IBM+Plex+Mono:wght@400;500;600&family=Inter:wght@400;500;600;700&display=swap');
* { box-sizing: border-box; }
body { margin: 0; }
.pqa-root { font-family: 'Inter', sans-serif; }
.pqa-display { font-family: 'Archivo', sans-serif; font-stretch: 115%; }
.pqa-mono { font-family: 'IBM Plex Mono', monospace; }
.pqa-fade { animation: pqaFade .35s ease; }
@keyframes pqaFade { from { opacity: 0; transform: translateY(6px);} to { opacity: 1; transform: none;} }
button:focus-visible { outline: 3px solid ${T.cobalt}; outline-offset: 2px; }
@media (prefers-reduced-motion: reduce) { .pqa-fade { animation: none; } }
`;

/* ---------------- THE SEVEN QUESTION CATEGORIES ---------------- */
const CATEGORIES = [
  {
    id: "go",
    depth: "00",
    name: "Go / No-Go",
    governing: "Do we need to talk about this?",
    color: "#5B6472",
    why: "Not everything deserves discussion. Go/No-Go questions test importance, willingness, and approach before you spend the room's time. Skipping this is why meetings drift.",
    stems: [
      "Is this important enough to discuss now?",
      "Are you willing to be questioned on this?",
      "What's the goal of this conversation — decide, inform, or explore?",
      "What are the ground rules? How much time do we have?",
      "What happens after we finish this discussion?",
    ],
    coach: "In recruiting: use at the top of every intake or debrief. 'Before we debrief — are we deciding today, or calibrating?' saves 20 minutes.",
  },
  {
    id: "clarify",
    depth: "01",
    name: "Clarification",
    governing: "What exactly do you mean?",
    color: "#2247E6",
    why: "Vagueness and ambiguity are where bad decisions hide. Clarification questions dissolve them: pin down terms, quantities, timeframes, and slices of the data.",
    stems: [
      "What do you mean by ___? Can you give an example?",
      "When you say 'soon' / 'strong' / 'a lot' — how much, by when?",
      "Graph question: is this trending up, down, or flat over time?",
      "Pivot question: show it to me by team / level / location / source.",
      "Which part specifically is harder than expected?",
    ],
    coach: "'We're not seeing strong candidates' → 'Strong on which dimension — research depth, coding, or communication? For which of the five roles?'",
  },
  {
    id: "assume",
    depth: "02",
    name: "Assumptions",
    governing: "What are we assuming?",
    color: "#7A3FC1",
    why: "An assumption is something that must be true for the statement to be true — and it lives in what is NOT said. Phrase it gently: 'Are we assuming…?'",
    stems: [
      "Existence — are we assuming a problem actually exists?",
      "Uniqueness — are we assuming there's only one cause / one option?",
      "Measurement — are we assuming we can measure improvement?",
      "Value — are we assuming this is bad (or good)?",
      "Time / constancy — are we assuming it isn't changing over time?",
      "Possibility — are we assuming this can be done at all?",
    ],
    coach: "'We need to raise the comp band' assumes comp is why offers decline. 'Are we assuming candidates are declining on comp? What did the last five decline surveys actually say?'",
  },
  {
    id: "bcq",
    depth: "03",
    name: "Basic Critical Question",
    governing: "How do we know this is true?",
    color: "#B5720F",
    why: "The BCQ is the evidence layer. Two drill shafts: validity of the DATA itself, and credibility of the SOURCE it came from.",
    stems: [
      "What data supports that? How recent is it?",
      "How was that number measured? What's the sample?",
      "Who told you that? How would they know?",
      "Is that firsthand, or secondhand through someone's summary?",
      "What would change your mind about this?",
    ],
    coach: "'The market rate for ML scientists is up 15%' → 'Which survey, what date, which geography, which level? Is that base or total comp?'",
  },
  {
    id: "causes",
    depth: "04",
    name: "Causes",
    governing: "What's causing this?",
    color: "#1D7A4A",
    why: "'Why?' five times is vague. Precision cause questions specify a mechanism: sequence, trigger, contribution, and what changed.",
    stems: [
      "What sequence of events led to this?",
      "What changed right before this started?",
      "Of the possible causes, which contributes most?",
      "Is this cause within our control?",
      "If we removed that cause, would the problem stop?",
    ],
    coach: "'Pipeline dropped in March' → 'What changed in March — the req load, the sourcing channels, the team's capacity, or the market?'",
  },
  {
    id: "effects",
    depth: "05",
    name: "Effects",
    governing: "What will be the effects?",
    color: "#C14B8A",
    why: "You don't need to be the expert to test consequences. Effects questions surface magnitude, side-effects, and who is impacted — before you commit.",
    stems: [
      "If we do this, what happens first? Then what?",
      "What's the size of the impact — best case, worst case?",
      "Who is affected that isn't in this room?",
      "What breaks if this works better than expected?",
      "What's the effect of doing nothing?",
    ],
    coach: "'Let's require a take-home for all candidates' → 'What's the effect on senior passive candidates' conversion? On time-to-offer against our competitors?'",
  },
  {
    id: "action",
    depth: "06",
    name: "Action",
    governing: "What should be done?",
    color: "#B3362C",
    why: "The payoff layer. Action questions turn analysis into commitment: options, criteria, owners, timing.",
    stems: [
      "What are our options? What did we rule out, and why?",
      "What criteria decide between them?",
      "Who owns this, and by when?",
      "What's the smallest next step that tests the idea?",
      "How will we know it worked?",
    ],
    coach: "Close every debrief with one: 'So the action is: extend to candidate A by Friday, and I own the comp approval. Anything wrong with that sentence?'",
  },
];

/* ---------------- PRECISION ANSWERING ---------------- */
const ANSWER_FORMS = [
  { form: "Yes / No", note: "The first word answers the question. Context can follow — briefly." },
  { form: "A single fact", note: "One clean piece of information, not a story." },
  { form: "A number", note: "With its unit and date. '37 candidates, as of Friday.'" },
  { form: "“I don't know”", note: "A legitimate, credibility-preserving answer. Optionally add how you'll find out." },
  { form: "Single point + support", note: "Answer first, then ONE supporting point. Not three. One." },
];

const ANSWER_SINS = [
  { sin: "The wind-up", ex: "“Well, to give you some background, when we started this search back in Q1…”", fix: "Answer first. Background only if asked." },
  { sin: "Answering a different question", ex: "Q: “Can we add one more recruiter to this critical deliverable by Monday?” A: “The team has been working incredibly hard, and everyone is already stretched across the other searches…”", fix: "“Yes — one recruiter from the CDAO pod, starting Monday. Trade-off: her two open reqs slip a week.”" },
  { sin: "The everything answer", ex: "Five caveats, three tangents, and the actual answer buried in minute four.", fix: "One answer, one point. Let the questioner drill." },
  { sin: "Faking certainty", ex: "Guessing a number rather than saying “I don't know.”", fix: "“I don't know — I can have it by 3pm.” This builds credibility, not erodes it." },
];

/* ---------------- PRACTICE DRILLS ---------------- */
const DRILL_ITEMS = [
  { q: "“Are we assuming candidates decline mainly because of comp?”", answer: "assume", hint: "It surfaces an unstated belief that must be true." },
  { q: "“Which source told you Meta's team is open to moving — and how would they know?”", answer: "bcq", hint: "It's probing credibility of the source." },
  { q: "“Before we start — is this a decision meeting or a calibration meeting?”", answer: "go", hint: "It tests whether/how to have the conversation." },
  { q: "“When you say the pipeline is 'weak' — weak on volume, quality, or conversion?”", answer: "clarify", hint: "It's dissolving a vague word." },
  { q: "“If we add a take-home assessment, what happens to senior-candidate conversion?”", answer: "effects", hint: "It projects the consequence of an action." },
  { q: "“What changed in March, right before applications dropped?”", answer: "causes", hint: "It hunts the mechanism behind an observation." },
  { q: "“What's the smallest next step, who owns it, and by when?”", answer: "action", hint: "It converts analysis into commitment." },
  { q: "“Show me offer-accept rate by level and by business unit.”", answer: "clarify", hint: "A pivot-table question — slicing the data is clarification." },
  { q: "“Are we assuming this is one problem, and not three separate ones?”", answer: "assume", hint: "Uniqueness is a classic assumption category." },
  { q: "“What's the effect of doing nothing for a quarter?”", answer: "effects", hint: "Consequences — including of inaction." },
];

const REWRITE_ITEMS = [
  {
    question: "Did the candidate accept the offer?",
    bad: "So we've been in close contact all week, and her recruiter relationship is really strong. She had a competing offer from a hedge fund, which complicated the timeline, and her family situation…",
    good: "Not yet. She asked for 48 more hours — competing hedge-fund offer. I expect a decision Thursday.",
    why: "First word answers the question ('Not yet'), then a single supporting point. The drama is available if the questioner drills.",
  },
  {
    question: "How many PhD interns have signed for summer?",
    bad: "The intern program is going really well this year, much better than last year, the team has done amazing work on university relations…",
    good: "14 of 20 target, as of yesterday.",
    why: "A number, with its unit and date. Progress commentary only if asked.",
  },
  {
    question: "Why did we lose the Staff ML Scientist to the competitor?",
    bad: "Honestly the market is brutal right now, everyone is fighting for the same talent, and their brand in AI is very strong…",
    good: "I don't know yet — the decline call is tomorrow. My hypothesis is comp band, but I'll confirm by Friday.",
    why: "An honest 'I don't know' plus a labeled hypothesis and a date beats a confident guess.",
  },
];

/* ---------------- COMPONENTS ---------------- */

function Tag({ children, color }) {
  return (
    <span
      className="pqa-mono"
      style={{
        fontSize: 11, fontWeight: 600, letterSpacing: "0.08em",
        color: color || T.inkSoft, textTransform: "uppercase",
      }}
    >
      {children}
    </span>
  );
}

function Foundations() {
  const facts = [
    ["Created by", "Dennis Matthies & Dr. Monica Worline, Stanford University's Center for Teaching & Learning; first taught in the Stanford Philosophy Department in the 1990s."],
    ["The book", "Precision Questioning, Dennis Matthies, 1996 — Stanford CTL course reader (ISBN 978-1887981033). Long out of print; used copies surface on AbeBooks."],
    ["Who teaches it", "Vervago (co-founded by Matthies & Worline) and partner EnlivenWork hold the exclusive license. That's why public materials are scarce."],
    ["Pedigree", "Bill Gates required Microsoft staff to train in PQ+A after frustration with unanswered questions in meetings. Deep studies at Microsoft and Cypress Semiconductor; ~25 years of Stanford research on accelerated learning."],
    ["Intellectual roots", "A structured, modern descendant of the Socratic method: one question, one answer, drill only as deep as the decision requires — never personalizing (no blame, no shame)."],
  ];
  return (
    <div className="pqa-fade">
      <p style={{ fontSize: 16, lineHeight: 1.65, color: T.ink, maxWidth: 680, marginTop: 0 }}>
        Precision Questioning + Answering is a <strong>call-and-response discipline</strong>: the
        questioner asks one precise question at a time; the answerer gives one precise answer.
        The structure looks like a <em>mine with shafts and tunnels</em> — you drill some veins
        deep, ignore others entirely, and stop the moment you have what the decision needs.
      </p>
      <div style={{ display: "grid", gap: 10, marginTop: 20 }}>
        {facts.map(([k, v]) => (
          <div key={k} style={{
            display: "grid", gridTemplateColumns: "140px 1fr", gap: 16,
            background: T.panel, border: `1px solid ${T.line}`, borderRadius: 10, padding: "14px 18px",
          }}>
            <Tag color={T.cobalt}>{k}</Tag>
            <div style={{ fontSize: 14, lineHeight: 1.55, color: T.ink }}>{v}</div>
          </div>
        ))}
      </div>
      <div style={{
        marginTop: 20, background: T.amberSoft, border: `1px solid #E8D5AE`,
        borderRadius: 10, padding: "14px 18px", fontSize: 14, lineHeight: 1.6, color: "#6B4A0E",
      }}>
        <strong>Two governing principles.</strong> Be a <em>situational</em> questioner — context
        picks the question, not a script. And drill only as far as necessary — the goal is a
        high-quality decision, not an interrogation. In the wrong hands PQ becomes abusive;
        in a coach's hands, it becomes psychological safety with rigor.
      </div>
    </div>
  );
}

function DrillMap() {
  const [open, setOpen] = useState("clarify");
  const cat = CATEGORIES.find((c) => c.id === open);
  return (
    <div className="pqa-fade">
      <p style={{ fontSize: 15, color: T.inkSoft, marginTop: 0, maxWidth: 640, lineHeight: 1.6 }}>
        Seven strata, from surface to payoff. Select a layer to expose its question veins.
        In a live conversation you rarely visit all seven — you drill where the decision is soft.
      </p>
      <div style={{ display: "grid", gridTemplateColumns: "minmax(220px, 300px) 1fr", gap: 20, alignItems: "start" }}>
        {/* Drill shaft */}
        <div role="tablist" aria-label="Question categories" style={{ display: "grid", gap: 0, borderLeft: `3px solid ${T.line}` }}>
          {CATEGORIES.map((c) => {
            const active = c.id === open;
            return (
              <button
                key={c.id}
                role="tab"
                aria-selected={active}
                onClick={() => setOpen(c.id)}
                style={{
                  textAlign: "left", border: "none", cursor: "pointer",
                  background: active ? T.panel : "transparent",
                  borderLeft: `3px solid ${active ? c.color : "transparent"}`,
                  marginLeft: -3, padding: "12px 14px",
                  borderRadius: "0 8px 8px 0",
                  transition: "background .15s",
                }}
              >
                <div style={{ display: "flex", alignItems: "baseline", gap: 10 }}>
                  <span className="pqa-mono" style={{ fontSize: 11, color: c.color, fontWeight: 600 }}>
                    ▼ {c.depth}
                  </span>
                  <span className="pqa-display" style={{ fontSize: 15, fontWeight: active ? 800 : 600, color: T.ink }}>
                    {c.name}
                  </span>
                </div>
                <div style={{ fontSize: 12, color: T.inkSoft, marginTop: 2, fontStyle: "italic" }}>
                  {c.governing}
                </div>
              </button>
            );
          })}
        </div>
        {/* Vein detail */}
        <div key={cat.id} className="pqa-fade" style={{
          background: T.panel, border: `1px solid ${T.line}`, borderTop: `4px solid ${cat.color}`,
          borderRadius: 12, padding: "20px 24px",
        }}>
          <Tag color={cat.color}>Depth {cat.depth} — {cat.name}</Tag>
          <h3 className="pqa-display" style={{ margin: "6px 0 8px", fontSize: 24, fontWeight: 800, color: T.ink }}>
            “{cat.governing}”
          </h3>
          <p style={{ fontSize: 14, lineHeight: 1.6, color: T.inkSoft, marginTop: 0 }}>{cat.why}</p>
          <div style={{ display: "grid", gap: 8, marginTop: 14 }}>
            {cat.stems.map((s, i) => (
              <div key={i} className="pqa-mono" style={{
                fontSize: 13, lineHeight: 1.5, color: T.ink,
                background: T.bg, borderRadius: 8, padding: "10px 14px",
                borderLeft: `3px solid ${cat.color}`,
              }}>
                {s}
              </div>
            ))}
          </div>
          <div style={{
            marginTop: 16, fontSize: 13.5, lineHeight: 1.6, color: T.ink,
            background: T.cobaltSoft, borderRadius: 8, padding: "12px 16px",
          }}>
            <strong style={{ color: T.cobalt }}>Coach's application:</strong> {cat.coach}
          </div>
        </div>
      </div>
    </div>
  );
}

function Answers() {
  const [revealed, setRevealed] = useState({});
  return (
    <div className="pqa-fade">
      <p style={{ fontSize: 15, color: T.inkSoft, marginTop: 0, maxWidth: 660, lineHeight: 1.6 }}>
        Precision Answering is the half most people skip — and the half Bill Gates cared about.
        The rule: <strong style={{ color: T.ink }}>the first word of your answer answers the question.</strong>{" "}
        There are only five legitimate answer shapes.
      </p>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(200px, 1fr))", gap: 10 }}>
        {ANSWER_FORMS.map((a) => (
          <div key={a.form} style={{ background: T.panel, border: `1px solid ${T.line}`, borderRadius: 10, padding: "14px 16px" }}>
            <div className="pqa-display" style={{ fontWeight: 800, fontSize: 16, color: T.cobalt }}>{a.form}</div>
            <div style={{ fontSize: 13, color: T.inkSoft, marginTop: 6, lineHeight: 1.5 }}>{a.note}</div>
          </div>
        ))}
      </div>

      <h3 className="pqa-display" style={{ fontSize: 18, fontWeight: 800, margin: "28px 0 10px", color: T.ink }}>
        The four answering sins
      </h3>
      <div style={{ display: "grid", gap: 10 }}>
        {ANSWER_SINS.map((s) => (
          <div key={s.sin} style={{
            background: T.panel, border: `1px solid ${T.line}`, borderRadius: 10, padding: "14px 18px",
            display: "grid", gridTemplateColumns: "160px 1fr", gap: 16,
          }}>
            <Tag color={T.red}>{s.sin}</Tag>
            <div>
              <div style={{ fontSize: 13.5, color: T.inkSoft, fontStyle: "italic", lineHeight: 1.5 }}>{s.ex}</div>
              <div style={{ fontSize: 13.5, color: T.green, marginTop: 6, lineHeight: 1.5 }}>
                <strong>Fix:</strong> {s.fix}
              </div>
            </div>
          </div>
        ))}
      </div>

      <h3 className="pqa-display" style={{ fontSize: 18, fontWeight: 800, margin: "28px 0 10px", color: T.ink }}>
        Rewrite lab — tap to reveal the precision version
      </h3>
      <div style={{ display: "grid", gap: 12 }}>
        {REWRITE_ITEMS.map((r, i) => (
          <div key={i} style={{ background: T.panel, border: `1px solid ${T.line}`, borderRadius: 12, padding: "16px 20px" }}>
            <Tag color={T.cobalt}>Question asked</Tag>
            <div className="pqa-mono" style={{ fontSize: 14, fontWeight: 600, color: T.ink, margin: "4px 0 10px" }}>
              “{r.question}”
            </div>
            <div style={{ fontSize: 13.5, color: T.red, lineHeight: 1.55 }}>
              <strong>The answer given:</strong> <span style={{ fontStyle: "italic", color: T.inkSoft }}>“{r.bad}”</span>
            </div>
            {revealed[i] ? (
              <div className="pqa-fade" style={{ marginTop: 12 }}>
                <div style={{ background: "#EAF6EF", border: "1px solid #C4E3D0", borderRadius: 8, padding: "12px 16px", fontSize: 14, color: T.green, lineHeight: 1.55 }}>
                  <strong>Precision version:</strong> “{r.good}”
                </div>
                <div style={{ fontSize: 13, color: T.inkSoft, marginTop: 8, lineHeight: 1.55 }}>{r.why}</div>
              </div>
            ) : (
              <button
                onClick={() => setRevealed({ ...revealed, [i]: true })}
                style={{
                  marginTop: 12, background: T.ink, color: "#fff", border: "none",
                  borderRadius: 8, padding: "8px 16px", fontSize: 13, fontWeight: 600,
                  cursor: "pointer", fontFamily: "'Inter', sans-serif",
                }}
              >
                Reveal precision answer
              </button>
            )}
          </div>
        ))}
      </div>
    </div>
  );
}

function Drills() {
  const [idx, setIdx] = useState(0);
  const [picked, setPicked] = useState(null);
  const [score, setScore] = useState(0);
  const [done, setDone] = useState(false);
  const [showHint, setShowHint] = useState(false);
  const item = DRILL_ITEMS[idx];
  const correct = picked === item.answer;

  const pick = (id) => {
    if (picked) return;
    setPicked(id);
    if (id === item.answer) setScore((s) => s + 1);
  };
  const next = () => {
    if (idx + 1 >= DRILL_ITEMS.length) { setDone(true); return; }
    setIdx(idx + 1); setPicked(null); setShowHint(false);
  };
  const restart = () => { setIdx(0); setPicked(null); setScore(0); setDone(false); setShowHint(false); };

  if (done) {
    const pct = Math.round((score / DRILL_ITEMS.length) * 100);
    return (
      <div className="pqa-fade" style={{ textAlign: "center", padding: "40px 0" }}>
        <div className="pqa-display" style={{ fontSize: 56, fontWeight: 900, color: pct >= 80 ? T.green : T.amber }}>
          {score}/{DRILL_ITEMS.length}
        </div>
        <p style={{ fontSize: 16, color: T.inkSoft, maxWidth: 480, margin: "8px auto 20px", lineHeight: 1.6 }}>
          {pct >= 80
            ? "Sharp. You can name the category as fast as you hear the question — that's the reflex that lets you drill deliberately in live meetings."
            : "Good drilling. Revisit the Toolkit tab, then run the drill again — category recognition is a reflex built by repetition."}
        </p>
        <button onClick={restart} style={{ background: T.cobalt, color: "#fff", border: "none", borderRadius: 8, padding: "10px 22px", fontSize: 14, fontWeight: 600, cursor: "pointer" }}>
          Run it again
        </button>
      </div>
    );
  }

  return (
    <div className="pqa-fade">
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 14 }}>
        <Tag color={T.cobalt}>Classify the question — {idx + 1} of {DRILL_ITEMS.length}</Tag>
        <Tag color={T.green}>Score {score}</Tag>
      </div>
      {/* progress */}
      <div style={{ height: 4, background: T.line, borderRadius: 2, marginBottom: 20 }}>
        <div style={{ height: 4, width: `${(idx / DRILL_ITEMS.length) * 100}%`, background: T.cobalt, borderRadius: 2, transition: "width .3s" }} />
      </div>
      <div className="pqa-mono" style={{
        fontSize: 17, fontWeight: 600, lineHeight: 1.55, color: T.ink,
        background: T.panel, border: `1px solid ${T.line}`, borderRadius: 12, padding: "22px 26px",
      }}>
        {item.q}
      </div>
      {!picked && (
        <button onClick={() => setShowHint(true)} style={{ marginTop: 10, background: "transparent", border: "none", color: T.cobalt, fontSize: 13, cursor: "pointer", padding: 0, fontWeight: 600 }}>
          {showHint ? "" : "Need a hint?"}
        </button>
      )}
      {showHint && !picked && (
        <div className="pqa-fade" style={{ fontSize: 13, color: T.amber, marginTop: 6 }}>{item.hint}</div>
      )}
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(150px, 1fr))", gap: 8, marginTop: 18 }}>
        {CATEGORIES.map((c) => {
          const isAnswer = c.id === item.answer;
          const isPicked = c.id === picked;
          let bg = T.panel, border = T.line, color = T.ink;
          if (picked) {
            if (isAnswer) { bg = "#EAF6EF"; border = T.green; color = T.green; }
            else if (isPicked) { bg = "#FBEAE8"; border = T.red; color = T.red; }
            else { color = T.inkSoft; }
          }
          return (
            <button key={c.id} onClick={() => pick(c.id)} disabled={!!picked}
              style={{
                background: bg, border: `2px solid ${border}`, borderRadius: 10,
                padding: "12px 10px", cursor: picked ? "default" : "pointer",
                fontFamily: "'Inter', sans-serif", fontSize: 13.5, fontWeight: 600, color,
                transition: "all .15s",
              }}>
              {c.name}
            </button>
          );
        })}
      </div>
      {picked && (
        <div className="pqa-fade" style={{ marginTop: 16, display: "flex", justifyContent: "space-between", alignItems: "center", gap: 16, flexWrap: "wrap" }}>
          <div style={{ fontSize: 14, color: correct ? T.green : T.red, fontWeight: 600 }}>
            {correct ? "Correct." : `Not quite — this is a ${CATEGORIES.find(c => c.id === item.answer).name} question.`}{" "}
            <span style={{ color: T.inkSoft, fontWeight: 400 }}>{item.hint}</span>
          </div>
          <button onClick={next} style={{ background: T.ink, color: "#fff", border: "none", borderRadius: 8, padding: "10px 22px", fontSize: 14, fontWeight: 600, cursor: "pointer", flexShrink: 0 }}>
            {idx + 1 >= DRILL_ITEMS.length ? "See score" : "Next →"}
          </button>
        </div>
      )}
    </div>
  );
}

function CoachCorner() {
  const moves = [
    ["Open with Go/No-Go", "“Is this the right conversation, and are you open to being questioned on it?” Getting consent makes drilling feel like partnership, not attack."],
    ["One question at a time", "Stacked questions get the weakest one answered. Ask one, wait, listen to the full answer, then choose the next shaft."],
    ["Never personalize", "Drill the thinking, not the person. “What's the evidence?” — never “Why didn't you check?” The moment blame enters, precision leaves."],
    ["Reward ‘I don't know’", "If people get punished for not knowing, they'll fabricate. Treat a clean ‘I don't know + how I'll find out’ as a high-credibility answer, out loud."],
    ["Stop at the decision", "The mine metaphor: drill only as deep as the decision requires. Coaching isn't a demonstration of your questioning stamina."],
    ["Model precision answering", "When your coachee questions YOU, answer first-word-first. They will mirror what you do faster than what you teach."],
  ];
  const practice = [
    ["Email triage", "Pick one long, convoluted email chain. Find the PQ+A gap at its heart — usually a vague term or an untested assumption. Reply with one precision question."],
    ["Meeting rep", "In your next debrief, silently label each question you hear by category. Notice which of the seven strata your team never visits."],
    ["Decision drill", "Take one live decision. Write the governing question for each of the 7 categories. Answer only the ones the decision actually needs."],
  ];
  return (
    <div className="pqa-fade">
      <h3 className="pqa-display" style={{ fontSize: 18, fontWeight: 800, margin: "0 0 12px", color: T.ink }}>Six coaching moves</h3>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(280px, 1fr))", gap: 10 }}>
        {moves.map(([k, v], i) => (
          <div key={k} style={{ background: T.panel, border: `1px solid ${T.line}`, borderRadius: 10, padding: "16px 18px" }}>
            <div className="pqa-display" style={{ fontWeight: 800, fontSize: 15, color: T.cobalt, marginBottom: 6 }}>{k}</div>
            <div style={{ fontSize: 13.5, color: T.inkSoft, lineHeight: 1.6 }}>{v}</div>
          </div>
        ))}
      </div>
      <h3 className="pqa-display" style={{ fontSize: 18, fontWeight: 800, margin: "26px 0 12px", color: T.ink }}>Daily practice grounds</h3>
      <div style={{ display: "grid", gap: 10 }}>
        {practice.map(([k, v]) => (
          <div key={k} style={{ display: "grid", gridTemplateColumns: "130px 1fr", gap: 16, background: T.panel, border: `1px solid ${T.line}`, borderRadius: 10, padding: "14px 18px" }}>
            <Tag color={T.amber}>{k}</Tag>
            <div style={{ fontSize: 13.5, color: T.ink, lineHeight: 1.6 }}>{v}</div>
          </div>
        ))}
      </div>
      <div style={{ marginTop: 20, background: T.panel, border: `1px solid ${T.line}`, borderRadius: 10, padding: "14px 18px", fontSize: 13, color: T.inkSoft, lineHeight: 1.7 }}>
        <strong style={{ color: T.ink }}>Go deeper:</strong> Matthies, <em>Precision Questioning</em> (Stanford CTL, 1996) ·
        vervago.com Skill Sharpeners archive · Wikipedia: “Precision questioning” ·
        Vervago's SWE 2011 workshop deck (SlideShare) · JD Meier's PQ/PA essays at sourcesofinsight.com.
        This guide is an independent study aid; Precision Q+A® training is delivered exclusively by Vervago / EnlivenWork.
      </div>
    </div>
  );
}

const TABS = [
  { id: "found", label: "Foundations", comp: Foundations },
  { id: "map", label: "Question Toolkit", comp: DrillMap },
  { id: "answers", label: "Precision Answers", comp: Answers },
  { id: "drills", label: "Practice Drills", comp: Drills },
  { id: "coach", label: "Coach's Corner", comp: CoachCorner },
];

export default function PQAGuide() {
  const [tab, setTab] = useState("found");
  const Active = TABS.find((t) => t.id === tab).comp;
  return (
    <div className="pqa-root" style={{ minHeight: "100vh", background: T.bg, color: T.ink }}>
      <style>{FONT_LINK}</style>
      {/* Header */}
      <header style={{ background: T.ink, padding: "34px 28px 26px" }}>
        <div style={{ maxWidth: 960, margin: "0 auto" }}>
          <Tag color="#8FA3FF">Drill only as deep as the decision requires</Tag>
          <h1 className="pqa-display" style={{ color: "#fff", fontSize: "clamp(28px, 5vw, 44px)", fontWeight: 900, margin: "6px 0 4px", letterSpacing: "-0.01em" }}>
            Precision Q<span style={{ color: "#8FA3FF" }}>+</span>A
          </h1>
          <p style={{ color: "#B9BFCC", fontSize: 14.5, margin: 0, maxWidth: 620, lineHeight: 1.6 }}>
            An interactive coaching guide to Precision Questioning &amp; Answering —
            the Stanford-born discipline of Dennis Matthies &amp; Monica Worline (Vervago),
            famously mandated by Bill Gates at Microsoft.
          </p>
        </div>
      </header>
      {/* Tabs */}
      <nav style={{ background: T.panel, borderBottom: `1px solid ${T.line}`, position: "sticky", top: 0, zIndex: 5 }}>
        <div style={{ maxWidth: 960, margin: "0 auto", display: "flex", overflowX: "auto" }}>
          {TABS.map((t) => (
            <button key={t.id} onClick={() => setTab(t.id)}
              style={{
                background: "transparent", border: "none",
                borderBottom: `3px solid ${tab === t.id ? T.cobalt : "transparent"}`,
                padding: "14px 18px", fontSize: 14, fontWeight: tab === t.id ? 700 : 500,
                color: tab === t.id ? T.cobalt : T.inkSoft, cursor: "pointer",
                whiteSpace: "nowrap", fontFamily: "'Inter', sans-serif",
              }}>
              {t.label}
            </button>
          ))}
        </div>
      </nav>
      {/* Body */}
      <main style={{ maxWidth: 960, margin: "0 auto", padding: "28px 28px 60px" }}>
        <Active />
      </main>
    </div>
  );
}
