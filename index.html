import { useState, useRef, useEffect } from "react";

/* ─────────────────────────────────────────────
   ADWISE CANADA — Production Landing Page
   Design: Editorial dark luxury, sharp typography
   Font: Clash Display + DM Sans feel via CSS
   Color: Deep navy-black + electric amber accent
───────────────────────────────────────────── */

const SYSTEM_PROMPT = `You are the AdWise AI consultant — a sharp, confident advisor for small Canadian businesses who want to run effective advertising without hiring an agency.

Your job: have a natural conversation to collect key info, then deliver a personalized ad strategy.

Collect (ONE question at a time, conversationally):
1. Business type and location (city/province)
2. Main goal (more customers, calls, bookings, online sales)
3. Target customer (who buys from them)
4. Monthly ad budget in CAD
5. Do they have a website? Ask for URL. If no site → recommend AdWise build one ($299 CAD, 5 days)
6. Preferred platforms OR let AI decide

After collecting all info, deliver a PERSONALIZED CAMPAIGN PLAN:
- Recommended platforms with reasoning
- Budget split (e.g. 70% Meta, 30% Google)
- Target audience specifics
- Ad format recommendations
- Expected results (leads/month estimate)
- Clear next step: "Click 'Launch My Campaign' to get started"

Tone: Direct, confident, friendly. Like a smart friend who knows marketing. No fluff. Use $ CAD amounts. Keep messages concise — 2-4 sentences max per message unless delivering the final plan.`;

const STATS = [
  { num: "3 min", label: "Average setup time" },
  { num: "4.8×", label: "Average ROI for clients" },
  { num: "500+", label: "Canadian businesses served" },
  { num: "$149", label: "Starting at CAD/mo" },
];

const NICHES = [
  { icon: "🔨", title: "Contractors & Trades", desc: "Roofing, HVAC, renovation, plumbing. High-ticket jobs, targeted local reach.", roi: "Up to 20× ROI" },
  { icon: "🦷", title: "Dental & Medical", desc: "Fill your calendar with new patients. Target by location and demographics.", roi: "Up to 15× ROI" },
  { icon: "🍽️", title: "Restaurants & Cafés", desc: "Drive foot traffic and reservations. Hyper-local targeting within 5km.", roi: "Up to 8× ROI" },
  { icon: "⚖️", title: "Law Firms", desc: "Generate qualified consultations. Precision targeting by legal need.", roi: "Up to 25× ROI" },
  { icon: "🏋️", title: "Fitness & Wellness", desc: "Memberships, classes, and bookings. Seasonal campaigns that convert.", roi: "Up to 10× ROI" },
  { icon: "🏡", title: "Real Estate Agents", desc: "Listings and buyer leads. Target active movers in your market.", roi: "Up to 30× ROI" },
];

const PLANS = [
  {
    name: "Starter",
    price: "149",
    desc: "Perfect for local shops and restaurants",
    color: "#F5A623",
    features: ["1 platform (Meta or Google)", "AI campaign setup", "Up to $1,000 ad budget", "Weekly performance report", "Email support"],
  },
  {
    name: "Growth",
    price: "349",
    desc: "Most popular for contractors & clinics",
    color: "#00E5FF",
    popular: true,
    features: ["Meta + Google Ads", "Competitor analysis", "Up to $5,000 ad budget", "Auto-optimization weekly", "Live chat support", "Website audit included"],
  },
  {
    name: "Pro",
    price: "699",
    desc: "For high-spend, multi-location businesses",
    color: "#B8FF57",
    features: ["Meta + Google + TikTok", "Unlimited ad budget", "Priority AI optimization", "Dedicated account AI", "Phone support", "Custom monthly report"],
  },
];

const HOW = [
  { n: "01", title: "Tell us about your business", body: "Chat with our AI for 3 minutes. Describe your business, goals, and budget. No forms, no jargon." },
  { n: "02", title: "AI analyzes your market", body: "We study your competitors' ads, identify winning audiences, and build your campaign strategy." },
  { n: "03", title: "Connect your ad account", body: "One click to connect Facebook or Google. Your money goes directly to the platform — we never touch it." },
  { n: "04", title: "Campaigns launch automatically", body: "AdWise creates and launches your ads via API. You get a dashboard with live results." },
];

export default function AdWiseCanada() {
  const [view, setView] = useState("landing"); // landing | chat
  const [messages, setMessages] = useState([
    {
      role: "assistant",
      content: "Hey! I'm AdWise — your AI advertising consultant.\n\nI'll get your business in front of the right customers in under 5 minutes. No agencies, no complexity.\n\nLet's start: what kind of business do you run, and where are you located?",
    },
  ]);
  const [input, setInput] = useState("");
  const [loading, setLoading] = useState(false);
  const [history, setHistory] = useState([]);
  const [step, setStep] = useState(1);
  const [menuOpen, setMenuOpen] = useState(false);
  const bottomRef = useRef(null);
  const inputRef = useRef(null);

  useEffect(() => {
    bottomRef.current?.scrollIntoView({ behavior: "smooth" });
  }, [messages, loading]);

  const detectStep = (text) => {
    const t = text.toLowerCase();
    if (t.includes("goal") || t.includes("objective") || t.includes("result")) return 2;
    if (t.includes("customer") || t.includes("audience") || t.includes("who")) return 3;
    if (t.includes("budget") || t.includes("spend") || t.includes("cad")) return 4;
    if (t.includes("website") || t.includes("url") || t.includes("site")) return 5;
    if (t.includes("platform") || t.includes("facebook") || t.includes("google") || t.includes("instagram")) return 6;
    if (t.includes("campaign") || t.includes("launch") || t.includes("recommend") || t.includes("plan")) return 7;
    return null;
  };

  const send = async () => {
    if (!input.trim() || loading) return;
    const userMsg = { role: "user", content: input.trim() };
    const newHist = [...history, userMsg];
    setMessages(m => [...m, userMsg]);
    setHistory(newHist);
    setInput("");
    setLoading(true);
    try {
      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 1000,
          system: SYSTEM_PROMPT,
          messages: newHist,
        }),
      });
      const data = await res.json();
      const reply = data.content?.map(b => b.text || "").join("") || "Something went wrong. Please try again.";
      const aMsg = { role: "assistant", content: reply };
      setMessages(m => [...m, aMsg]);
      setHistory(h => [...h, aMsg]);
      const s = detectStep(reply);
      if (s && s > step) setStep(s);
    } catch {
      setMessages(m => [...m, { role: "assistant", content: "Connection error. Please try again." }]);
    }
    setLoading(false);
    setTimeout(() => inputRef.current?.focus(), 50);
  };

  const onKey = (e) => {
    if (e.key === "Enter" && !e.shiftKey) { e.preventDefault(); send(); }
  };

  const STEPS = ["Business", "Goals", "Audience", "Budget", "Website", "Platforms", "Your Plan"];

  /* ── CHAT VIEW ── */
  if (view === "chat") return (
    <div style={C.chatWrap}>
      <style>{chatKeyframes}</style>
      {/* Chat Nav */}
      <div style={C.chatNav}>
        <button onClick={() => setView("landing")} style={C.backBtn}>← Back</button>
        <div style={C.chatNavBrand}>
          <div style={C.chatNavDot} />
          <span style={C.chatNavName}>AdWise <span style={C.chatNavSub}>Canada</span></span>
        </div>
        <div style={C.chatNavStatus}>
          <div style={C.statusPulse} />
          <span style={C.statusText}>AI Online</span>
        </div>
      </div>

      {/* Progress Steps */}
      <div style={C.progress}>
        {STEPS.map((s, i) => (
          <div key={s} style={C.progressItem}>
            <div style={{
              ...C.progressDot,
              background: step > i + 1 ? "#F5A623" : step === i + 1 ? "#F5A623" : "rgba(255,255,255,0.1)",
              boxShadow: step === i + 1 ? "0 0 16px #F5A623" : "none",
              transform: step === i + 1 ? "scale(1.2)" : "scale(1)",
            }}>
              {step > i + 1 ? "✓" : i + 1}
            </div>
            <span style={{ ...C.progressLabel, color: step >= i + 1 ? "#F5A623" : "rgba(255,255,255,0.25)" }}>{s}</span>
          </div>
        ))}
      </div>

      {/* Messages */}
      <div style={C.msgs}>
        {messages.map((m, i) => (
          <div key={i} style={{ display: "flex", justifyContent: m.role === "user" ? "flex-end" : "flex-start", marginBottom: 14, animation: "fadeUp 0.3s ease" }}>
            {m.role === "assistant" && <div style={C.avatar}>W</div>}
            <div style={m.role === "user" ? C.userBubble : C.aiBubble}>
              {m.content.split("\n").map((line, j) => (
                <span key={j}>{line}{j < m.content.split("\n").length - 1 && <br />}</span>
              ))}
            </div>
          </div>
        ))}
        {loading && (
          <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 14 }}>
            <div style={C.avatar}>W</div>
            <div style={C.typingBox}>
              <span style={{ ...C.typingDot, animationDelay: "0s" }} />
              <span style={{ ...C.typingDot, animationDelay: "0.2s" }} />
              <span style={{ ...C.typingDot, animationDelay: "0.4s" }} />
            </div>
          </div>
        )}
        <div ref={bottomRef} />
      </div>

      {/* Input */}
      <div style={C.inputWrap}>
        <textarea
          ref={inputRef}
          value={input}
          onChange={e => setInput(e.target.value)}
          onKeyDown={onKey}
          placeholder="Type your message..."
          rows={1}
          style={C.textarea}
          autoFocus
        />
        <button onClick={send} disabled={loading || !input.trim()} style={{ ...C.sendBtn, opacity: loading || !input.trim() ? 0.4 : 1 }}>
          ↑
        </button>
      </div>
    </div>
  );

  /* ── LANDING VIEW ── */
  return (
    <div style={L.root}>
      <style>{landingCSS}</style>

      {/* ── NAV ── */}
      <nav style={L.nav}>
        <div style={L.navBrand}>
          <span style={L.navLogo}>AdWise</span>
          <span style={L.navCountry}>Canada</span>
        </div>
        <div style={L.navLinks}>
          {["How it works", "Industries", "Pricing"].map(l => (
            <a key={l} href={`#${l.toLowerCase().replace(/ /g, "-")}`} style={L.navLink}>{l}</a>
          ))}
        </div>
        <button style={L.navCta} onClick={() => setView("chat")}>
          Start Free →
        </button>
      </nav>

      {/* ── HERO ── */}
      <section style={L.hero}>
        {/* Background grid */}
        <div style={L.heroBg} />
        <div style={L.heroGlow} />

        <div style={L.heroInner}>
          <div style={L.heroBadge}>
            <span style={L.heroBadgeDot} />
            AI-Powered · Canadian Businesses Only
          </div>

          <h1 style={L.heroH1}>
            Your ads.<br />
            <span style={L.heroAccent}>Launched in minutes.</span><br />
            Not months.
          </h1>

          <p style={L.heroP}>
            AdWise is the AI that runs your Meta, Google, and TikTok ads — automatically. Tell us your goal, connect your account, and watch customers come in. No agency. No complexity. Just results.
          </p>

          <div style={L.heroCtas}>
            <button className="cta-primary" style={L.ctaPrimary} onClick={() => setView("chat")}>
              Launch My First Campaign
              <span style={L.ctaArrow}>→</span>
            </button>
            <div style={L.ctaNote}>Free to start · No credit card required</div>
          </div>

          {/* Stats row */}
          <div style={L.statsRow}>
            {STATS.map((s, i) => (
              <div key={i} style={L.statItem}>
                <div style={L.statNum}>{s.num}</div>
                <div style={L.statLabel}>{s.label}</div>
              </div>
            ))}
          </div>
        </div>

        {/* Hero visual — chat preview */}
        <div style={L.heroVisual}>
          <div style={L.chatPreview}>
            <div style={L.cpHeader}>
              <div style={L.cpDots}>
                <div style={{ ...L.cpDot, background: "#FF5F57" }} />
                <div style={{ ...L.cpDot, background: "#FFBD2E" }} />
                <div style={{ ...L.cpDot, background: "#28CA41" }} />
              </div>
              <div style={L.cpTitle}>AdWise AI</div>
              <div style={L.cpLive}><div style={L.cpLiveDot} /> Live</div>
            </div>
            <div style={L.cpBody}>
              {[
                { ai: true, msg: "Hey! What kind of business do you run?" },
                { ai: false, msg: "Dental clinic in Calgary" },
                { ai: true, msg: "Perfect. What's your monthly ad budget?" },
                { ai: false, msg: "Around $800 CAD" },
                { ai: true, msg: "Got it. Analyzing competitors in Calgary..." },
              ].map((m, i) => (
                <div key={i} style={{ display: "flex", justifyContent: m.ai ? "flex-start" : "flex-end", marginBottom: 8 }}>
                  <div style={m.ai ? L.cpAiBubble : L.cpUserBubble}>{m.msg}</div>
                </div>
              ))}
              <div style={L.cpTyping}>
                <div style={L.cpTypingDot} />
                <div style={{ ...L.cpTypingDot, animationDelay: "0.2s" }} />
                <div style={{ ...L.cpTypingDot, animationDelay: "0.4s" }} />
              </div>
            </div>
          </div>

          {/* Floating cards */}
          <div style={{ ...L.floatCard, top: 20, right: -20 }}>
            <div style={L.floatIcon}>📈</div>
            <div>
              <div style={L.floatTitle}>Campaign Live</div>
              <div style={L.floatSub}>18 leads this week</div>
            </div>
          </div>
          <div style={{ ...L.floatCard, bottom: 40, left: -30 }}>
            <div style={L.floatIcon}>💰</div>
            <div>
              <div style={L.floatTitle}>Cost per lead</div>
              <div style={L.floatSub}>$12.40 CAD avg</div>
            </div>
          </div>
        </div>
      </section>

      {/* ── HOW IT WORKS ── */}
      <section id="how-it-works" style={L.section}>
        <div style={L.sectionInner}>
          <div style={L.sectionEyebrow}>How it works</div>
          <h2 style={L.sectionH2}>From conversation<br />to live campaign</h2>
          <div style={L.howGrid}>
            {HOW.map((h, i) => (
              <div key={i} className="how-card" style={L.howCard}>
                <div style={L.howNum}>{h.n}</div>
                <h3 style={L.howTitle}>{h.title}</h3>
                <p style={L.howBody}>{h.body}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* ── INDUSTRIES ── */}
      <section id="industries" style={{ ...L.section, background: "rgba(255,255,255,0.015)" }}>
        <div style={L.sectionInner}>
          <div style={L.sectionEyebrow}>Industries</div>
          <h2 style={L.sectionH2}>Built for Canadian<br />small businesses</h2>
          <div style={L.nicheGrid}>
            {NICHES.map((n, i) => (
              <div key={i} className="niche-card" style={L.nicheCard}>
                <div style={L.nicheIcon}>{n.icon}</div>
                <div style={L.nicheRoi}>{n.roi}</div>
                <h3 style={L.nicheTitle}>{n.title}</h3>
                <p style={L.nicheDesc}>{n.desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* ── PRICING ── */}
      <section id="pricing" style={L.section}>
        <div style={L.sectionInner}>
          <div style={L.sectionEyebrow}>Pricing</div>
          <h2 style={L.sectionH2}>Simple, transparent<br />pricing in CAD</h2>
          <p style={L.pricingNote}>Your ad budget goes directly to Meta/Google. We only charge for the platform.</p>
          <div style={L.plansGrid}>
            {PLANS.map((p, i) => (
              <div key={i} className="plan-card" style={{ ...L.planCard, ...(p.popular ? L.planCardPop : {}), borderColor: p.popular ? p.color : "rgba(255,255,255,0.08)" }}>
                {p.popular && <div style={{ ...L.planBadge, background: p.color, color: "#08090E" }}>Most Popular</div>}
                <div style={{ ...L.planName, color: p.color }}>{p.name}</div>
                <div style={L.planPriceRow}>
                  <span style={L.planDollar}>$</span>
                  <span style={L.planPrice}>{p.price}</span>
                  <span style={L.planPer}> CAD/mo</span>
                </div>
                <div style={L.planDesc}>{p.desc}</div>
                <div style={L.planDivider} />
                {p.features.map((f, j) => (
                  <div key={j} style={L.planFeature}>
                    <span style={{ color: p.color, fontWeight: 700 }}>✓</span>
                    <span>{f}</span>
                  </div>
                ))}
                <button
                  onClick={() => setView("chat")}
                  style={{ ...L.planBtn, background: p.popular ? p.color : "transparent", color: p.popular ? "#08090E" : p.color, borderColor: p.color }}
                >
                  Get Started
                </button>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* ── FINAL CTA ── */}
      <section style={L.ctaSection}>
        <div style={L.ctaGlow} />
        <div style={L.ctaInner}>
          <div style={L.sectionEyebrow}>Ready?</div>
          <h2 style={L.ctaH2}>Stop losing customers<br />to competitors who advertise.</h2>
          <p style={L.ctaP}>Join 500+ Canadian businesses running smarter ads with AdWise. Setup takes 3 minutes.</p>
          <button className="cta-primary" style={{ ...L.ctaPrimary, fontSize: 18, padding: "18px 48px" }} onClick={() => setView("chat")}>
            Launch My Campaign Free →
          </button>
          <div style={L.ctaLogos}>
            {["Meta", "Google", "TikTok", "Instagram"].map(l => (
              <span key={l} style={L.ctaLogo}>{l}</span>
            ))}
          </div>
        </div>
      </section>

      {/* ── FOOTER ── */}
      <footer style={L.footer}>
        <div style={L.footerBrand}>
          <span style={L.navLogo}>AdWise</span>
          <span style={L.navCountry}>Canada</span>
        </div>
        <div style={L.footerLinks}>
          {["Privacy Policy", "Terms of Service", "Contact"].map(l => (
            <span key={l} style={L.footerLink}>{l}</span>
          ))}
        </div>
        <div style={L.footerCopy}>© 2025 AdWise Canada. All rights reserved.</div>
      </footer>
    </div>
  );
}

/* ─── CHAT STYLES ─── */
const C = {
  chatWrap: { height: "100vh", display: "flex", flexDirection: "column", background: "#08090E", color: "#fff", fontFamily: "'DM Sans', sans-serif" },
  chatNav: { display: "flex", alignItems: "center", justifyContent: "space-between", padding: "14px 24px", borderBottom: "1px solid rgba(255,255,255,0.07)", background: "rgba(8,9,14,0.98)" },
  backBtn: { background: "none", border: "1px solid rgba(255,255,255,0.12)", color: "rgba(255,255,255,0.5)", padding: "7px 14px", borderRadius: 8, cursor: "pointer", fontSize: 13, fontFamily: "inherit" },
  chatNavBrand: { display: "flex", alignItems: "center", gap: 8 },
  chatNavDot: { width: 32, height: 32, borderRadius: "50%", background: "linear-gradient(135deg, #F5A623, #FF6B35)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 14, fontWeight: 900, color: "#fff" },
  chatNavName: { fontSize: 17, fontWeight: 800, color: "#fff" },
  chatNavSub: { color: "#F5A623" },
  chatNavStatus: { display: "flex", alignItems: "center", gap: 6 },
  statusPulse: { width: 8, height: 8, borderRadius: "50%", background: "#4ADE80", boxShadow: "0 0 8px #4ADE80" },
  statusText: { fontSize: 12, color: "rgba(255,255,255,0.45)" },
  progress: { display: "flex", padding: "12px 20px", borderBottom: "1px solid rgba(255,255,255,0.05)", gap: 4, overflowX: "auto", background: "rgba(255,255,255,0.01)" },
  progressItem: { display: "flex", flexDirection: "column", alignItems: "center", gap: 4, flex: 1, minWidth: 55 },
  progressDot: { width: 28, height: 28, borderRadius: "50%", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 11, fontWeight: 800, color: "#08090E", transition: "all 0.3s" },
  progressLabel: { fontSize: 9, fontWeight: 600, textAlign: "center", transition: "color 0.3s", letterSpacing: 0.3 },
  msgs: { flex: 1, overflowY: "auto", padding: "20px 16px" },
  avatar: { width: 34, height: 34, borderRadius: "50%", background: "linear-gradient(135deg, #F5A623, #FF6B35)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 14, fontWeight: 900, color: "#fff", flexShrink: 0, marginRight: 10 },
  aiBubble: { background: "rgba(255,255,255,0.06)", border: "1px solid rgba(255,255,255,0.09)", borderRadius: "4px 16px 16px 16px", padding: "12px 16px", fontSize: 14, lineHeight: 1.65, maxWidth: "76%", color: "rgba(255,255,255,0.88)" },
  userBubble: { background: "linear-gradient(135deg, rgba(245,166,35,0.25), rgba(255,107,53,0.2))", border: "1px solid rgba(245,166,35,0.3)", borderRadius: "16px 4px 16px 16px", padding: "12px 16px", fontSize: 14, lineHeight: 1.65, maxWidth: "76%", color: "#fff" },
  typingBox: { background: "rgba(255,255,255,0.06)", border: "1px solid rgba(255,255,255,0.09)", borderRadius: "4px 16px 16px 16px", padding: "14px 18px", display: "flex", gap: 5, alignItems: "center" },
  typingDot: { width: 7, height: 7, borderRadius: "50%", background: "#F5A623", display: "inline-block", animation: "bounce 1.2s infinite" },
  inputWrap: { display: "flex", gap: 10, padding: "14px 16px", borderTop: "1px solid rgba(255,255,255,0.07)", background: "rgba(255,255,255,0.02)" },
  textarea: { flex: 1, background: "rgba(255,255,255,0.06)", border: "1px solid rgba(255,255,255,0.12)", borderRadius: 12, padding: "12px 16px", fontSize: 15, color: "#fff", resize: "none", outline: "none", fontFamily: "inherit", lineHeight: 1.5 },
  sendBtn: { width: 48, height: 48, borderRadius: 12, background: "linear-gradient(135deg, #F5A623, #FF6B35)", border: "none", color: "#fff", fontSize: 20, fontWeight: 900, cursor: "pointer", flexShrink: 0, alignSelf: "flex-end", transition: "opacity 0.2s" },
};

/* ─── LANDING STYLES ─── */
const L = {
  root: { minHeight: "100vh", background: "#08090E", color: "#fff", fontFamily: "'DM Sans', 'Segoe UI', sans-serif", overflowX: "hidden" },
  nav: { display: "flex", alignItems: "center", justifyContent: "space-between", padding: "20px 48px", position: "sticky", top: 0, background: "rgba(8,9,14,0.92)", backdropFilter: "blur(16px)", borderBottom: "1px solid rgba(255,255,255,0.06)", zIndex: 200 },
  navBrand: { display: "flex", alignItems: "baseline", gap: 6 },
  navLogo: { fontSize: 22, fontWeight: 900, letterSpacing: "-0.5px", color: "#fff" },
  navCountry: { fontSize: 13, fontWeight: 600, color: "#F5A623", letterSpacing: 1, textTransform: "uppercase" },
  navLinks: { display: "flex", gap: 32 },
  navLink: { color: "rgba(255,255,255,0.45)", fontSize: 14, fontWeight: 500, textDecoration: "none", cursor: "pointer", transition: "color 0.2s" },
  navCta: { background: "#F5A623", color: "#08090E", border: "none", padding: "10px 24px", borderRadius: 8, fontWeight: 800, fontSize: 14, cursor: "pointer", fontFamily: "inherit", letterSpacing: "-0.2px" },

  hero: { display: "grid", gridTemplateColumns: "1fr 1fr", gap: 80, alignItems: "center", maxWidth: 1200, margin: "0 auto", padding: "80px 48px 100px", position: "relative", minHeight: "calc(100vh - 70px)" },
  heroBg: { position: "absolute", inset: 0, backgroundImage: "radial-gradient(circle at 20% 50%, rgba(245,166,35,0.04) 0%, transparent 50%), radial-gradient(circle at 80% 20%, rgba(0,229,255,0.03) 0%, transparent 50%)", pointerEvents: "none" },
  heroGlow: { position: "absolute", top: "30%", left: "50%", transform: "translate(-50%,-50%)", width: 600, height: 600, background: "radial-gradient(circle, rgba(245,166,35,0.06) 0%, transparent 70%)", pointerEvents: "none" },
  heroInner: { position: "relative", zIndex: 1 },
  heroBadge: { display: "inline-flex", alignItems: "center", gap: 8, background: "rgba(245,166,35,0.1)", border: "1px solid rgba(245,166,35,0.25)", borderRadius: 100, padding: "6px 16px", fontSize: 12, color: "#F5A623", fontWeight: 600, marginBottom: 28, letterSpacing: 0.3 },
  heroBadgeDot: { width: 6, height: 6, borderRadius: "50%", background: "#F5A623", boxShadow: "0 0 6px #F5A623" },
  heroH1: { fontSize: "clamp(38px, 5vw, 60px)", fontWeight: 900, lineHeight: 1.08, letterSpacing: "-2px", marginBottom: 24, color: "#fff" },
  heroAccent: { color: "#F5A623" },
  heroP: { fontSize: 17, color: "rgba(255,255,255,0.5)", lineHeight: 1.7, marginBottom: 40, maxWidth: 480 },
  heroCtas: { display: "flex", flexDirection: "column", gap: 12, alignItems: "flex-start", marginBottom: 56 },
  ctaPrimary: { display: "inline-flex", alignItems: "center", gap: 10, background: "#F5A623", color: "#08090E", border: "none", padding: "15px 32px", borderRadius: 10, fontWeight: 800, fontSize: 16, cursor: "pointer", fontFamily: "inherit", letterSpacing: "-0.3px", transition: "transform 0.2s, box-shadow 0.2s", boxShadow: "0 0 40px rgba(245,166,35,0.3)" },
  ctaArrow: { fontSize: 18 },
  ctaNote: { fontSize: 12, color: "rgba(255,255,255,0.3)" },
  statsRow: { display: "flex", gap: 40, paddingTop: 40, borderTop: "1px solid rgba(255,255,255,0.07)" },
  statItem: {},
  statNum: { fontSize: 32, fontWeight: 900, color: "#F5A623", letterSpacing: "-1px", lineHeight: 1 },
  statLabel: { fontSize: 12, color: "rgba(255,255,255,0.4)", marginTop: 4 },

  heroVisual: { position: "relative", display: "flex", justifyContent: "center", alignItems: "center" },
  chatPreview: { background: "rgba(255,255,255,0.04)", border: "1px solid rgba(255,255,255,0.1)", borderRadius: 20, overflow: "hidden", width: "100%", maxWidth: 400, boxShadow: "0 40px 80px rgba(0,0,0,0.5)" },
  cpHeader: { display: "flex", alignItems: "center", justifyContent: "space-between", padding: "14px 18px", borderBottom: "1px solid rgba(255,255,255,0.07)", background: "rgba(255,255,255,0.03)" },
  cpDots: { display: "flex", gap: 6 },
  cpDot: { width: 10, height: 10, borderRadius: "50%" },
  cpTitle: { fontSize: 14, fontWeight: 700, color: "rgba(255,255,255,0.7)" },
  cpLive: { display: "flex", alignItems: "center", gap: 5, fontSize: 11, color: "#4ADE80" },
  cpLiveDot: { width: 6, height: 6, borderRadius: "50%", background: "#4ADE80", boxShadow: "0 0 6px #4ADE80" },
  cpBody: { padding: "16px" },
  cpAiBubble: { background: "rgba(255,255,255,0.07)", borderRadius: "4px 12px 12px 12px", padding: "8px 12px", fontSize: 13, color: "rgba(255,255,255,0.8)", maxWidth: "80%", lineHeight: 1.5 },
  cpUserBubble: { background: "rgba(245,166,35,0.2)", border: "1px solid rgba(245,166,35,0.25)", borderRadius: "12px 4px 12px 12px", padding: "8px 12px", fontSize: 13, color: "#fff", maxWidth: "80%", lineHeight: 1.5 },
  cpTyping: { display: "flex", gap: 5, padding: "8px 12px", background: "rgba(255,255,255,0.07)", borderRadius: "4px 12px 12px 12px", width: "fit-content", marginTop: 8 },
  cpTypingDot: { width: 6, height: 6, borderRadius: "50%", background: "#F5A623", animation: "bounce 1.2s infinite" },
  floatCard: { position: "absolute", background: "rgba(8,9,14,0.9)", border: "1px solid rgba(255,255,255,0.1)", borderRadius: 12, padding: "12px 16px", display: "flex", alignItems: "center", gap: 10, backdropFilter: "blur(12px)", boxShadow: "0 8px 32px rgba(0,0,0,0.4)" },
  floatIcon: { fontSize: 22 },
  floatTitle: { fontSize: 13, fontWeight: 700, color: "#fff" },
  floatSub: { fontSize: 11, color: "rgba(255,255,255,0.45)", marginTop: 2 },

  section: { padding: "100px 0" },
  sectionInner: { maxWidth: 1200, margin: "0 auto", padding: "0 48px" },
  sectionEyebrow: { fontSize: 11, fontWeight: 700, color: "#F5A623", textTransform: "uppercase", letterSpacing: 2, marginBottom: 14 },
  sectionH2: { fontSize: "clamp(32px, 4vw, 52px)", fontWeight: 900, letterSpacing: "-1.5px", lineHeight: 1.08, marginBottom: 56, color: "#fff" },

  howGrid: { display: "grid", gridTemplateColumns: "repeat(4, 1fr)", gap: 24 },
  howCard: { background: "rgba(255,255,255,0.03)", border: "1px solid rgba(255,255,255,0.07)", borderRadius: 16, padding: "28px 24px", transition: "border-color 0.3s, transform 0.3s", cursor: "default" },
  howNum: { fontSize: 48, fontWeight: 900, color: "rgba(245,166,35,0.2)", lineHeight: 1, marginBottom: 16 },
  howTitle: { fontSize: 16, fontWeight: 800, marginBottom: 10, color: "#fff", letterSpacing: "-0.3px" },
  howBody: { fontSize: 14, color: "rgba(255,255,255,0.45)", lineHeight: 1.65 },

  nicheGrid: { display: "grid", gridTemplateColumns: "repeat(3, 1fr)", gap: 18 },
  nicheCard: { background: "rgba(255,255,255,0.03)", border: "1px solid rgba(255,255,255,0.07)", borderRadius: 16, padding: "28px 24px", transition: "all 0.3s", cursor: "default" },
  nicheIcon: { fontSize: 36, marginBottom: 12 },
  nicheRoi: { display: "inline-block", background: "rgba(245,166,35,0.1)", border: "1px solid rgba(245,166,35,0.2)", borderRadius: 100, padding: "3px 10px", fontSize: 11, color: "#F5A623", fontWeight: 700, marginBottom: 12 },
  nicheTitle: { fontSize: 17, fontWeight: 800, marginBottom: 8, color: "#fff" },
  nicheDesc: { fontSize: 13, color: "rgba(255,255,255,0.45)", lineHeight: 1.6 },

  pricingNote: { fontSize: 15, color: "rgba(255,255,255,0.4)", marginTop: -32, marginBottom: 48 },
  plansGrid: { display: "grid", gridTemplateColumns: "repeat(3, 1fr)", gap: 20 },
  planCard: { background: "rgba(255,255,255,0.03)", border: "1px solid", borderRadius: 18, padding: "32px 28px", position: "relative", transition: "transform 0.2s" },
  planCardPop: { background: "rgba(0,229,255,0.04)", boxShadow: "0 0 60px rgba(0,229,255,0.08)" },
  planBadge: { position: "absolute", top: -13, left: "50%", transform: "translateX(-50%)", fontSize: 11, fontWeight: 800, padding: "4px 14px", borderRadius: 100, whiteSpace: "nowrap", letterSpacing: 0.3 },
  planName: { fontSize: 12, fontWeight: 800, textTransform: "uppercase", letterSpacing: 1.5, marginBottom: 10 },
  planPriceRow: { display: "flex", alignItems: "baseline", marginBottom: 6 },
  planDollar: { fontSize: 24, fontWeight: 900, color: "rgba(255,255,255,0.6)", marginRight: 2 },
  planPrice: { fontSize: 56, fontWeight: 900, letterSpacing: "-3px", color: "#fff", lineHeight: 1 },
  planPer: { fontSize: 14, color: "rgba(255,255,255,0.35)", marginLeft: 4 },
  planDesc: { fontSize: 13, color: "rgba(255,255,255,0.4)", marginBottom: 20, lineHeight: 1.5 },
  planDivider: { height: 1, background: "rgba(255,255,255,0.07)", marginBottom: 20 },
  planFeature: { display: "flex", gap: 10, fontSize: 14, color: "rgba(255,255,255,0.7)", marginBottom: 10, alignItems: "flex-start" },
  planBtn: { width: "100%", marginTop: 24, padding: "13px", borderRadius: 10, border: "1.5px solid", fontWeight: 800, fontSize: 14, cursor: "pointer", fontFamily: "inherit", transition: "all 0.2s", letterSpacing: "-0.2px" },

  ctaSection: { padding: "120px 48px", textAlign: "center", position: "relative", overflow: "hidden" },
  ctaGlow: { position: "absolute", top: "50%", left: "50%", transform: "translate(-50%,-50%)", width: 800, height: 400, background: "radial-gradient(ellipse, rgba(245,166,35,0.08) 0%, transparent 70%)", pointerEvents: "none" },
  ctaInner: { position: "relative", zIndex: 1, maxWidth: 700, margin: "0 auto" },
  ctaH2: { fontSize: "clamp(32px, 5vw, 56px)", fontWeight: 900, letterSpacing: "-2px", lineHeight: 1.05, marginBottom: 20, marginTop: 14 },
  ctaP: { fontSize: 17, color: "rgba(255,255,255,0.45)", marginBottom: 40, lineHeight: 1.6 },
  ctaLogos: { display: "flex", justifyContent: "center", gap: 24, marginTop: 32 },
  ctaLogo: { fontSize: 13, color: "rgba(255,255,255,0.2)", fontWeight: 600, letterSpacing: 0.5 },

  footer: { display: "flex", justifyContent: "space-between", alignItems: "center", padding: "24px 48px", borderTop: "1px solid rgba(255,255,255,0.06)", flexWrap: "wrap", gap: 12 },
  footerBrand: { display: "flex", alignItems: "baseline", gap: 6 },
  footerLinks: { display: "flex", gap: 24 },
  footerLink: { fontSize: 13, color: "rgba(255,255,255,0.3)", cursor: "pointer" },
  footerCopy: { fontSize: 12, color: "rgba(255,255,255,0.2)" },
};

const chatKeyframes = `
  @keyframes fadeUp { from { opacity:0; transform:translateY(8px); } to { opacity:1; transform:translateY(0); } }
  @keyframes bounce { 0%,80%,100% { transform:translateY(0); } 40% { transform:translateY(-6px); } }
`;

const landingCSS = `
  @keyframes bounce { 0%,80%,100% { transform:translateY(0); } 40% { transform:translateY(-6px); } }
  @keyframes float { 0%,100% { transform:translateY(0px); } 50% { transform:translateY(-8px); } }
  .cta-primary:hover { transform: translateY(-2px); box-shadow: 0 0 60px rgba(245,166,35,0.45) !important; }
  .how-card:hover { border-color: rgba(245,166,35,0.3) !important; transform: translateY(-4px); }
  .niche-card:hover { border-color: rgba(245,166,35,0.25) !important; transform: translateY(-4px); }
  .plan-card:hover { transform: translateY(-4px); }
  a:hover { color: rgba(255,255,255,0.85) !important; }
`;
