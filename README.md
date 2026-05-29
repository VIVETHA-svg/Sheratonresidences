import { useState } from "react";

const data = {
  usp: [
    { icon: "🌍", tag: "GLOBAL RARITY", title: "GCC's First & Only Sheraton Residences", body: "One of just five Sheraton-branded residences in the entire world — and the only one in the GCC. Competing projects on Al Marjan Island (Nikki Beach by Aldar, JW Marriott, Janu by Aman) are newer announcements still in early stages. We launched first and are ahead on the construction timeline.", highlight: "5 Sheraton Residences worldwide. Only 1 in the GCC." },
    { icon: "🏖️", tag: "EXCLUSIVE ACCESS", title: "Private Beach — A True Rarity on Al Marjan Island", body: "Only 30% of off-plan projects on Al Marjan Island offer beach access at all. Within our project, direct access to the private beach is exclusively reserved for residents of The Residences — not shared with the general public or hotel guests. This is a lifestyle differentiator that commands premium resale and rental value.", highlight: "Only 30% of projects on the island offer beach access. Ours is private & exclusive to residents." },
    { icon: "📍", tag: "PRIME POSITIONING", title: "Treasure Island — Closer to Wynn Than the Competition", body: "We are located on Treasure Island — the most strategically positioned of Al Marjan's four islands, placing us significantly closer to the Wynn Resort & Casino (opening 2027) than the majority of competing projects, which are saturated on The View Island. Proximity to the UAE's first integrated resort is a direct driver of rental demand, capital appreciation, and lifestyle value.", highlight: "Treasure Island location = closer to Wynn than most competitors on The View Island." },
    { icon: "📐", tag: "PREMIUM SIZES", title: "Generous Unit Sizes — A Powerful Resale Advantage", body: "With only 159 units, this is a low-density development — creating exclusivity and long-term scarcity value. Unit sizes are premium across all types: Studios from 725–755 sq ft, 1-Bedrooms from 968–1,089 sq ft, 2-Bedrooms from 1,142–1,392 sq ft. Larger-than-average sizes mean investors benefit at resale — bigger units command higher prices per transaction and attract end-users alongside investors.", highlight: "159 units only. Studios start at 725 sq ft — well above market average." },
    { icon: "💰", tag: "VALUE PRICING", title: "Price Stable Since Launch — AED 2,800/sq ft", body: "The project has not increased its price since launch, starting at AED 2,800/sq ft. Most branded residences on Al Marjan Island are overpriced relative to what they deliver. We offer a Marriott-Sheraton branded beachfront asset at a competitive entry point — giving buyers room to grow and giving brokers a genuinely easy conversation with price-conscious investors.", highlight: "Priced from AED 2,800/sq ft — stable since launch, below most branded competitors." },
    { icon: "🏗️", tag: "CONSTRUCTION CONFIDENCE", title: "In-House Construction Arm — Milestone Transparency", body: "Our in-house construction team manages every phase from foundation to finish, eliminating the delays and miscommunications that plague third-party contractors. Construction progress is updated publicly every time we reach a milestone. This is critical for international investors who need trust signals — and equally important for brokers whose credibility rests on accurate delivery promises.", highlight: "Real-time milestone updates. In-house team = no outsourced delays." },
    { icon: "✈️", tag: "GLOBAL LIFESTYLE", title: "Marriott ONVIA Platform — 7,000+ Hotels Worldwide", body: "Ownership here goes far beyond the unit. Through Marriott International's ONVIA platform, residents receive global owner recognition, preferred rates across 7,000+ Marriott hotels worldwide, priority upgrades, and exclusive travel privileges. No competing project on Al Marjan Island offers this level of global hospitality integration to owners.", highlight: "ONVIA: exclusive lifestyle and travel benefits across Marriott's global portfolio." },
    { icon: "📈", tag: "INVESTMENT RETURNS", title: "Strong Capital Growth + Rental Yield Potential", body: "Al Marjan Island apartments appreciated ~33% in 2024 and ~20% in 2025. Once the island's resorts are fully operational, rental returns are forecast at 7–8% per annum on long-term basis, with select short-term rental projects already achieving 9–12.6% gross yields. Branded, fully furnished, hotel-managed residences consistently outperform unbranded equivalents in both occupancy and rate.", highlight: "33% price growth in 2024. Rental yields projected at 7–12% once Wynn opens." },
  ],
  renders: [
    {
      label: "Kitchen & Dining",
      icon: "🍽️",
      tag: "CULINARY SPACE",
      headline: "European-Finish Kitchen with Marble & Oak",
      bullets: [
        "Handleless oak cabinetry floor-to-ceiling — warm, hotel-grade quality",
        "Marble splashback with under-cabinet LED lighting",
        "Integrated appliances including built-in oven and smart coffee system",
        "Oval pedestal dining table beneath a sculptural black pendant — designer-specified, not generic",
        "Herringbone hardwood flooring throughout — a finish typically seen only in AED 4,000+/sq ft projects",
      ],
      pitch: "The kitchen alone will close price-sensitive clients. The finish level exceeds what competitors at this price point are delivering.",
    },
    {
      label: "Master Bedroom",
      icon: "🛏️",
      tag: "MASTER SUITE",
      headline: "Unobstructed Sea View from Every Bedroom",
      bullets: [
        "Floor-to-ceiling glazing framing direct Arabian Gulf views — the sea is the artwork",
        "Upholstered headboard wall with textured linen panelling — boutique hotel execution",
        "Herringbone hardwood floors matching the kitchen — design coherence throughout",
        "Pendant bedside lighting, bespoke sculptural wall art — curated, not catalogue",
        "Private balcony visible through full-height sliding doors",
      ],
      pitch: "The sea view is non-negotiable for end-users. Buyers who see this render convert. Lead with it on WhatsApp.",
    },
    {
      label: "Living Room",
      icon: "🛋️",
      tag: "LIVING AREA",
      headline: "Panoramic Sea Views with Luxury Living Finishes",
      bullets: [
        "Corner sea-view orientation — horizon visible from every seat in the room",
        "Warm oak joinery feature wall with integrated backlit shelving",
        "Layered material palette: linen walls, hardwood floors, textured rugs",
        "Designer-specified furniture package included — move-in ready for rental",
        "Sheer curtains frame the view without blocking it — thoughtful interior detailing",
      ],
      pitch: "The living room communicates lifestyle instantly. For rental investors, a furnished unit at this quality level commands a significant premium over unfurnished stock.",
    },
  ],
  floorplan: {
    seaViewUnits: ["1-BHK Type-1 (×4)", "2-BHK Type-1 (×1)", "Studio Type-1M (×1)", "2-BHK Type-1M (×1)", "1-BHK Type-1M (×1)"],
    islandViewUnits: ["1-BHK Type-2B (×1)", "1-BHK Type-2 (×1)", "2-BHK Type-1B (×1)", "1-BHK Type-1M (×3)", "2-BHK Type-2 (×1)", "1-BHK Type-2M (×1)", "1-BHK Type-2 (×1)", "Studio Type-1 (×1)", "2-BHK Type-3 (×1)"],
  },
  paymentPlan: [
    { type: "Studios & 2-Bedrooms", plan: "40 / 60", color: "#C9A96E", rows: [{ milestone: "Booking / Reservation", pct: "5%", note: "" }, { milestone: "SPA Signing", pct: "5%", note: "SPA issued at 10% (vs. industry standard 20%)" }, { milestone: "Construction Installments", pct: "30%", note: "10 quarterly installments" }, { milestone: "Handover (Q3 2028)", pct: "60%", note: "" }] },
    { type: "1-Bedrooms", plan: "30 / 70", color: "#5B8DB8", rows: [{ milestone: "Booking / Reservation", pct: "5%", note: "" }, { milestone: "SPA Signing", pct: "5%", note: "SPA issued at 10% (vs. industry standard 20%)" }, { milestone: "Construction Installments", pct: "20%", note: "10 quarterly installments" }, { milestone: "Handover (Q3 2028)", pct: "70%", note: "" }] },
  ],
};

const tagColors = { "GLOBAL RARITY": "#8B6914", "EXCLUSIVE ACCESS": "#1a6b4a", "PRIME POSITIONING": "#4a1a6b", "PREMIUM SIZES": "#1a4a6b", "VALUE PRICING": "#6b1a1a", "CONSTRUCTION CONFIDENCE": "#3d5c1a", "GLOBAL LIFESTYLE": "#1a4a5c", "INVESTMENT RETURNS": "#5c3d1a" };
const tagLight = { "GLOBAL RARITY": "#C9A96E", "EXCLUSIVE ACCESS": "#4dbb8a", "PRIME POSITIONING": "#9a6ab8", "PREMIUM SIZES": "#4a8ab8", "VALUE PRICING": "#b85c5c", "CONSTRUCTION CONFIDENCE": "#7aaa3d", "GLOBAL LIFESTYLE": "#3d8aaa", "INVESTMENT RETURNS": "#aa7a3d" };

const TABS = ["Overview", "Interiors", "Floor Plan", "Payment Plan", "Commission"];

export default function BrokerBrief() {
  const [tab, setTab] = useState(0);
  const [expanded, setExpanded] = useState(null);
  const [expandedRender, setExpandedRender] = useState(0);

  return (
    <div style={{ fontFamily: "'Georgia','Times New Roman',serif", background: "linear-gradient(135deg,#0a0a0a 0%,#111418 50%,#0d1117 100%)", minHeight: "100vh", color: "#e8dcc8" }}>
      {/* Header */}
      <div style={{ background: "#0a0a0a", borderBottom: "1px solid #C9A96E33", padding: "36px 28px 28px", position: "relative", overflow: "hidden" }}>
        <div style={{ position: "absolute", inset: 0, backgroundImage: "radial-gradient(ellipse at 20% 50%,#C9A96E08 0%,transparent 60%)" }} />
        <div style={{ position: "relative", maxWidth: 860, margin: "0 auto" }}>
          <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 6 }}>
            <div style={{ height: 1, width: 32, background: "#C9A96E" }} />
            <span style={{ fontSize: 10, letterSpacing: "0.25em", color: "#C9A96E", fontFamily: "sans-serif", fontWeight: 600 }}>ATARA DEVELOPMENT · BROKER BRIEFING</span>
          </div>
          <h1 style={{ fontSize: "clamp(20px,4vw,34px)", fontWeight: 400, margin: "0 0 4px", color: "#f0e6cc" }}>
            The Residences at Sheraton<br /><span style={{ color: "#C9A96E" }}>Al Marjan Island</span>
          </h1>
          <div style={{ display: "flex", gap: 20, marginTop: 18, flexWrap: "wrap" }}>
            {[["159", "Exclusive Units"], ["Q3 2028", "Delivery"], ["AED 2,800", "Per sq ft from"], ["6–7%", "Commission"]].map(([v, l]) => (
              <div key={l} style={{ textAlign: "center" }}>
                <div style={{ fontSize: 18, fontWeight: 700, color: "#C9A96E", fontFamily: "sans-serif" }}>{v}</div>
                <div style={{ fontSize: 9, color: "#666", letterSpacing: "0.12em", fontFamily: "sans-serif" }}>{l.toUpperCase()}</div>
              </div>
            ))}
          </div>
        </div>
      </div>

      {/* Tabs */}
      <div style={{ background: "#0d0d0d", borderBottom: "1px solid #1a1a1a", padding: "0 28px", overflowX: "auto" }}>
        <div style={{ maxWidth: 860, margin: "0 auto", display: "flex", gap: 0 }}>
          {TABS.map((t, i) => (
            <button key={t} onClick={() => setTab(i)} style={{
              background: "none", border: "none", borderBottom: `2px solid ${tab === i ? "#C9A96E" : "transparent"}`,
              color: tab === i ? "#C9A96E" : "#555", padding: "14px 18px", fontSize: 11,
              letterSpacing: "0.15em", fontFamily: "sans-serif", fontWeight: 600, cursor: "pointer", whiteSpace: "nowrap",
            }}>{t.toUpperCase()}</button>
          ))}
        </div>
      </div>

      <div style={{ maxWidth: 860, margin: "0 auto", padding: "32px 24px" }}>

        {/* TAB 0: Overview */}
        {tab === 0 && (
          <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
            <div style={{ fontSize: 11, letterSpacing: "0.2em", color: "#C9A96E", fontFamily: "sans-serif", fontWeight: 600, marginBottom: 8 }}>— KEY STRENGTHS & UNIQUE SELLING POINTS</div>
            {data.usp.map((item, i) => {
              const isOpen = expanded === i;
              const tc = tagColors[item.tag] || "#555";
              const tl = tagLight[item.tag] || "#C9A96E";
              return (
                <div key={i} onClick={() => setExpanded(isOpen ? null : i)} style={{ background: isOpen ? "linear-gradient(135deg,#1a1a1a,#161a1f)" : "#131313", border: `1px solid ${isOpen ? "#C9A96E44" : "#222"}`, borderLeft: `3px solid ${isOpen ? "#C9A96E" : "#333"}`, borderRadius: 8, padding: "16px 20px", cursor: "pointer" }}>
                  <div style={{ display: "flex", alignItems: "flex-start", gap: 12 }}>
                    <span style={{ fontSize: 20, flexShrink: 0, marginTop: 2 }}>{item.icon}</span>
                    <div style={{ flex: 1 }}>
                      <div style={{ display: "flex", alignItems: "center", gap: 8, flexWrap: "wrap", marginBottom: 4 }}>
                        <span style={{ fontSize: 9, letterSpacing: "0.2em", fontFamily: "sans-serif", fontWeight: 700, background: tc + "22", color: tl, padding: "2px 7px", borderRadius: 3, border: `1px solid ${tc}44` }}>{item.tag}</span>
                        <span style={{ fontSize: "clamp(12px,2vw,14px)", fontWeight: 600, color: "#f0e6cc" }}>{item.title}</span>
                      </div>
                      {!isOpen && <div style={{ fontSize: 11, color: "#C9A96E", fontFamily: "sans-serif", background: "#C9A96E11", padding: "5px 10px", borderRadius: 4, display: "inline-block", marginTop: 3, fontStyle: "italic" }}>{item.highlight}</div>}
                      {isOpen && (
                        <div style={{ marginTop: 8 }}>
                          <p style={{ fontSize: 13, color: "#bbb", lineHeight: 1.7, fontFamily: "sans-serif", margin: "0 0 10px" }}>{item.body}</p>
                          <div style={{ fontSize: 11, color: "#C9A96E", fontFamily: "sans-serif", background: "#C9A96E11", padding: "7px 12px", borderRadius: 4, borderLeft: "3px solid #C9A96E", fontStyle: "italic" }}>💡 {item.highlight}</div>
                        </div>
                      )}
                    </div>
                    <span style={{ color: "#444", fontSize: 14, flexShrink: 0 }}>{isOpen ? "▲" : "▼"}</span>
                  </div>
                </div>
              );
            })}
          </div>
        )}

        {/* TAB 1: Interiors */}
        {tab === 1 && (
          <div>
            <div style={{ fontSize: 11, letterSpacing: "0.2em", color: "#C9A96E", fontFamily: "sans-serif", fontWeight: 600, marginBottom: 8 }}>— INTERIOR RENDERS & SALES TALKING POINTS</div>
            <p style={{ fontSize: 12, color: "#666", fontFamily: "sans-serif", marginBottom: 20, fontStyle: "italic" }}>Use these finish descriptions and broker pitch notes when presenting to clients or on listing pages.</p>

            {/* Render Selector */}
            <div style={{ display: "flex", gap: 8, marginBottom: 20, flexWrap: "wrap" }}>
              {data.renders.map((r, i) => (
                <button key={i} onClick={() => setExpandedRender(i)} style={{
                  background: expandedRender === i ? "#C9A96E" : "#131313",
                  border: `1px solid ${expandedRender === i ? "#C9A96E" : "#333"}`,
                  color: expandedRender === i ? "#0a0a0a" : "#aaa",
                  padding: "8px 16px", borderRadius: 6, cursor: "pointer",
                  fontSize: 12, fontFamily: "sans-serif", fontWeight: expandedRender === i ? 700 : 400,
                }}>
                  {r.icon} {r.label}
                </button>
              ))}
            </div>

            {data.renders.map((r, i) => expandedRender !== i ? null : (
              <div key={i} style={{ background: "#131313", border: "1px solid #C9A96E33", borderRadius: 10, overflow: "hidden" }}>
                {/* Visual placeholder */}
                <div style={{
                  background: "linear-gradient(135deg,#1a1510 0%,#0f1520 50%,#101510 100%)",
                  height: 200, display: "flex", alignItems: "center", justifyContent: "center",
                  borderBottom: "1px solid #222", position: "relative", overflow: "hidden",
                }}>
                  <div style={{ position: "absolute", inset: 0, backgroundImage: "radial-gradient(ellipse at 30% 60%,#C9A96E06 0%,transparent 70%), radial-gradient(ellipse at 70% 30%,#5B8DB806 0%,transparent 60%)" }} />
                  <div style={{ textAlign: "center", position: "relative" }}>
                    <div style={{ fontSize: 48, marginBottom: 8 }}>{r.icon}</div>
                    <div style={{ fontSize: 13, color: "#C9A96E", fontFamily: "sans-serif", letterSpacing: "0.15em" }}>{r.tag}</div>
                    <div style={{ fontSize: 16, color: "#f0e6cc", marginTop: 6, fontWeight: 500 }}>{r.headline}</div>
                    <div style={{ fontSize: 10, color: "#444", fontFamily: "sans-serif", marginTop: 10, letterSpacing: "0.1em" }}>RENDER AVAILABLE — SEE PROJECT MEDIA PACK</div>
                  </div>
                </div>

                <div style={{ padding: "22px 24px" }}>
                  <div style={{ fontSize: 11, color: "#C9A96E", letterSpacing: "0.15em", fontFamily: "sans-serif", marginBottom: 12 }}>FINISH & DESIGN CALLOUTS</div>
                  <div style={{ display: "flex", flexDirection: "column", gap: 8, marginBottom: 20 }}>
                    {r.bullets.map((b, j) => (
                      <div key={j} style={{ display: "flex", gap: 10, alignItems: "flex-start" }}>
                        <span style={{ color: "#C9A96E", fontSize: 14, flexShrink: 0, marginTop: 1 }}>◆</span>
                        <span style={{ fontSize: 13, color: "#ccc", fontFamily: "sans-serif", lineHeight: 1.6 }}>{b}</span>
                      </div>
                    ))}
                  </div>
                  <div style={{ background: "#0d1a10", border: "1px solid #2a5a2a", borderRadius: 8, padding: "14px 18px" }}>
                    <div style={{ fontSize: 10, color: "#5c8c5c", letterSpacing: "0.15em", fontFamily: "sans-serif", marginBottom: 6 }}>💬 BROKER PITCH NOTE</div>
                    <p style={{ fontSize: 13, color: "#8cb88c", fontFamily: "sans-serif", margin: 0, lineHeight: 1.6, fontStyle: "italic" }}>{r.pitch}</p>
                  </div>
                </div>
              </div>
            ))}
          </div>
        )}

        {/* TAB 2: Floor Plan */}
        {tab === 2 && (
          <div>
            <div style={{ fontSize: 11, letterSpacing: "0.2em", color: "#C9A96E", fontFamily: "sans-serif", fontWeight: 600, marginBottom: 8 }}>— TYPICAL FLOOR PLAN · 3RD–10TH FLOORS</div>
            <p style={{ fontSize: 12, color: "#666", fontFamily: "sans-serif", marginBottom: 20, fontStyle: "italic" }}>The building is oriented with Sea View to the north and Island View to the south. Every unit has a meaningful view.</p>

            {/* Orientation Banner */}
            <div style={{ background: "#0a1520", border: "1px solid #1a3a5a", borderRadius: 8, padding: "10px 20px", textAlign: "center", marginBottom: 16, fontSize: 13, color: "#5B8DB8", fontFamily: "sans-serif", letterSpacing: "0.1em" }}>
              🌊 SEA VIEW — ARABIAN GULF (NORTH FACING)
            </div>

            {/* Floor Plan SVG */}
            <div style={{ background: "#131313", border: "1px solid #222", borderRadius: 10, padding: "24px 16px", marginBottom: 16 }}>
              <svg viewBox="0 0 760 320" xmlns="http://www.w3.org/2000/svg" style={{ width: "100%", height: "auto" }}>
                {/* Background */}
                <rect width="760" height="320" fill="#131313" />

                {/* LEFT WING */}
                {/* Sea-facing row (top) */}
                {[
                  { x: 10, y: 30, w: 72, h: 90, type: "1BHK", label: "1-BHK\nType-2B1", color: "#2a3d2a" },
                  { x: 84, y: 30, w: 78, h: 90, type: "2BHK", label: "2-BHK\nType-1M", color: "#1a2a3d" },
                  { x: 164, y: 30, w: 68, h: 90, type: "STUDIO", label: "Studio\nType-1M", color: "#2a2a2a" },
                  { x: 234, y: 30, w: 78, h: 90, type: "2BHK", label: "2-BHK\nType-1", color: "#1a2a3d" },
                  { x: 314, y: 30, w: 68, h: 90, type: "1BHK", label: "1-BHK\nType-1", color: "#2a3d2a" },
                  { x: 384, y: 30, w: 68, h: 90, type: "1BHK", label: "1-BHK\nType-1", color: "#2a3d2a" },
                  { x: 454, y: 30, w: 68, h: 90, type: "1BHK", label: "1-BHK\nType-1", color: "#2a3d2a" },
                ].map((u, i) => (
                  <g key={"tl" + i}>
                    <rect x={u.x} y={u.y} width={u.w} height={u.h} fill={u.color} stroke="#C9A96E44" strokeWidth="1" rx="2" />
                    {u.label.split("\n").map((ln, j) => (
                      <text key={j} x={u.x + u.w / 2} y={u.y + 38 + j * 14} textAnchor="middle" fill="#aaa" fontSize="9" fontFamily="sans-serif">{ln}</text>
                    ))}
                  </g>
                ))}

                {/* Core / Corridor */}
                <rect x={10} y={122} width={520} height={22} fill="#0d0d0d" stroke="#333" strokeWidth="1" />
                <text x={270} y={137} textAnchor="middle" fill="#555" fontSize="9" fontFamily="sans-serif">CORRIDOR / CORE</text>

                {/* Island-facing row (bottom) */}
                {[
                  { x: 10, y: 146, w: 78, h: 90, type: "1BHK", label: "1-BHK\nType-2B", color: "#2a3d2a" },
                  { x: 90, y: 146, w: 72, h: 90, type: "1BHK", label: "1-BHK\nType-2", color: "#2a3d2a" },
                  { x: 164, y: 146, w: 88, h: 90, type: "2BHK", label: "2-BHK\nType-1B", color: "#1a2a3d" },
                  { x: 254, y: 146, w: 58, h: 90, type: "LIFT", label: "LIFT\nLOBBY", color: "#111" },
                ].map((u, i) => (
                  <g key={"bl" + i}>
                    <rect x={u.x} y={u.y} width={u.w} height={u.h} fill={u.color} stroke="#C9A96E44" strokeWidth="1" rx="2" />
                    {u.label.split("\n").map((ln, j) => (
                      <text key={j} x={u.x + u.w / 2} y={u.y + 38 + j * 14} textAnchor="middle" fill="#aaa" fontSize="9" fontFamily="sans-serif">{ln}</text>
                    ))}
                  </g>
                ))}

                {/* RIGHT WING */}
                {/* Sea-facing row right */}
                {[
                  { x: 540, y: 30, w: 60, h: 90, type: "1BHK", label: "1-BHK\nType-1M", color: "#2a3d2a" },
                  { x: 602, y: 30, w: 60, h: 90, type: "1BHK", label: "1-BHK\nType-1M", color: "#2a3d2a" },
                  { x: 664, y: 30, w: 60, h: 90, type: "1BHK", label: "1-BHK\nType-1M", color: "#2a3d2a" },
                  { x: 726, y: 30, w: 30, h: 90, type: "2BHK", label: "2B", color: "#1a2a3d" },
                ].map((u, i) => (
                  <g key={"tr" + i}>
                    <rect x={u.x} y={u.y} width={u.w} height={u.h} fill={u.color} stroke="#C9A96E44" strokeWidth="1" rx="2" />
                    {u.label.split("\n").map((ln, j) => (
                      <text key={j} x={u.x + u.w / 2} y={u.y + 38 + j * 14} textAnchor="middle" fill="#aaa" fontSize="9" fontFamily="sans-serif">{ln}</text>
                    ))}
                  </g>
                ))}

                {/* Corridor right */}
                <rect x={540} y={122} width={216} height={22} fill="#0d0d0d" stroke="#333" strokeWidth="1" />

                {/* Island row right */}
                {[
                  { x: 540, y: 146, w: 62, h: 90, type: "1BHK", label: "1-BHK\nType-2M", color: "#2a3d2a" },
                  { x: 604, y: 146, w: 58, h: 90, type: "1BHK", label: "1-BHK\nType-2", color: "#2a3d2a" },
                  { x: 664, y: 146, w: 46, h: 90, type: "STUDIO", label: "Studio\nType-1", color: "#2a2a2a" },
                  { x: 712, y: 146, w: 44, h: 90, type: "2BHK", label: "2-BHK\nType-3", color: "#1a2a3d" },
                ].map((u, i) => (
                  <g key={"br" + i}>
                    <rect x={u.x} y={u.y} width={u.w} height={u.h} fill={u.color} stroke="#C9A96E44" strokeWidth="1" rx="2" />
                    {u.label.split("\n").map((ln, j) => (
                      <text key={j} x={u.x + u.w / 2} y={u.y + 38 + j * 14} textAnchor="middle" fill="#aaa" fontSize="9" fontFamily="sans-serif">{ln}</text>
                    ))}
                  </g>
                ))}

                {/* Compass */}
                <text x={740} y={295} textAnchor="middle" fill="#C9A96E" fontSize="18" fontFamily="sans-serif">N</text>
                <line x1={740} y1={300} x2={740} y2={316} stroke="#C9A96E" strokeWidth="1.5" />
                <polygon points="740,290 736,302 740,299 744,302" fill="#C9A96E" />

                {/* Legend */}
                <rect x={10} y={248} width={12} height={12} fill="#2a2a2a" stroke="#C9A96E44" strokeWidth="1" rx="1" />
                <text x={26} y={259} fill="#888" fontSize="10" fontFamily="sans-serif">Studio</text>
                <rect x={75} y={248} width={12} height={12} fill="#2a3d2a" stroke="#C9A96E44" strokeWidth="1" rx="1" />
                <text x={91} y={259} fill="#888" fontSize="10" fontFamily="sans-serif">1 Bedroom</text>
                <rect x={160} y={248} width={12} height={12} fill="#1a2a3d" stroke="#C9A96E44" strokeWidth="1" rx="1" />
                <text x={176} y={259} fill="#888" fontSize="10" fontFamily="sans-serif">2 Bedroom</text>

                <text x={380} y={280} textAnchor="middle" fill="#C9A96E" fontSize="11" fontFamily="sans-serif" letterSpacing="2">3RD – 10TH FLOOR · TYPICAL PLAN</text>
              </svg>
            </div>

            <div style={{ background: "#0a1520", border: "1px solid #1a3a5a", borderRadius: 8, padding: "10px 20px", textAlign: "center", marginBottom: 20, fontSize: 13, color: "#5B8DB8", fontFamily: "sans-serif", letterSpacing: "0.1em" }}>
              🏝️ ISLAND VIEW — AL MARJAN LAGOON (SOUTH FACING)
            </div>

            {/* View breakdown */}
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12 }}>
              {[
                { label: "Sea View Units", color: "#5B8DB8", icon: "🌊", units: data.floorplan.seaViewUnits },
                { label: "Island View Units", color: "#C9A96E", icon: "🏝️", units: data.floorplan.islandViewUnits },
              ].map(col => (
                <div key={col.label} style={{ background: "#131313", border: `1px solid ${col.color}33`, borderRadius: 8, padding: "16px" }}>
                  <div style={{ fontSize: 11, color: col.color, letterSpacing: "0.15em", fontFamily: "sans-serif", marginBottom: 10 }}>{col.icon} {col.label.toUpperCase()}</div>
                  {col.units.map((u, i) => (
                    <div key={i} style={{ fontSize: 12, color: "#999", fontFamily: "sans-serif", padding: "4px 0", borderBottom: i < col.units.length - 1 ? "1px solid #1a1a1a" : "none" }}>{u}</div>
                  ))}
                </div>
              ))}
            </div>
          </div>
        )}

        {/* TAB 3: Payment Plan */}
        {tab === 3 && (
          <div>
            <div style={{ fontSize: 11, letterSpacing: "0.2em", color: "#C9A96E", fontFamily: "sans-serif", fontWeight: 600, marginBottom: 20 }}>— PAYMENT PLAN</div>
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit,minmax(260px,1fr))", gap: 14 }}>
              {data.paymentPlan.map((plan, i) => (
                <div key={i} style={{ background: "#131313", border: `1px solid ${plan.color}33`, borderTop: `3px solid ${plan.color}`, borderRadius: 8, padding: "20px" }}>
                  <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 14 }}>
                    <div>
                      <div style={{ fontSize: 10, color: "#666", letterSpacing: "0.15em", fontFamily: "sans-serif", marginBottom: 3 }}>UNIT TYPE</div>
                      <div style={{ fontSize: 14, fontWeight: 600, color: "#f0e6cc" }}>{plan.type}</div>
                    </div>
                    <div style={{ textAlign: "right" }}>
                      <div style={{ fontSize: 10, color: "#666", letterSpacing: "0.15em", fontFamily: "sans-serif", marginBottom: 3 }}>SPLIT</div>
                      <div style={{ fontSize: 22, fontWeight: 700, color: plan.color, fontFamily: "sans-serif" }}>{plan.plan}</div>
                    </div>
                  </div>
                  <div style={{ borderTop: "1px solid #222", paddingTop: 12 }}>
                    {plan.rows.map((row, j) => (
                      <div key={j} style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", padding: "7px 0", borderBottom: j < plan.rows.length - 1 ? "1px solid #1a1a1a" : "none" }}>
                        <div>
                          <div style={{ fontSize: 12, color: "#ccc", fontFamily: "sans-serif" }}>{row.milestone}</div>
                          {row.note && <div style={{ fontSize: 10, color: "#C9A96E", fontFamily: "sans-serif", marginTop: 2, fontStyle: "italic" }}>{row.note}</div>}
                        </div>
                        <div style={{ fontSize: 16, fontWeight: 700, color: plan.color, fontFamily: "sans-serif", flexShrink: 0, marginLeft: 10 }}>{row.pct}</div>
                      </div>
                    ))}
                  </div>
                  <div style={{ marginTop: 12, background: plan.color + "11", border: `1px solid ${plan.color}33`, borderRadius: 6, padding: "7px 10px", fontSize: 10, color: plan.color, fontFamily: "sans-serif", fontStyle: "italic" }}>
                    ✅ SPA issued at 10% — vs. industry standard 20%
                  </div>
                </div>
              ))}
            </div>
            <div style={{ marginTop: 14, background: "#0d1a0d", border: "1px solid #2a4a2a", borderRadius: 8, padding: "14px 18px", fontSize: 12, color: "#8bc48b", fontFamily: "sans-serif" }}>
              <strong style={{ color: "#acd4ac" }}>DocuSign Integration:</strong> SPAs are executed fully online — clients sign from anywhere in the world via a secure email link. No courier delays, no paperwork friction.
            </div>
          </div>
        )}

        {/* TAB 4: Commission */}
        {tab === 4 && (
          <div>
            <div style={{ fontSize: 11, letterSpacing: "0.2em", color: "#C9A96E", fontFamily: "sans-serif", fontWeight: 600, marginBottom: 20 }}>— BROKER COMMISSION STRUCTURE</div>
            <div style={{ background: "linear-gradient(135deg,#131313,#0f1a10)", border: "1px solid #C9A96E33", borderRadius: 8, padding: "26px" }}>
              <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit,minmax(180px,1fr))", gap: 16, marginBottom: 22 }}>
                <div style={{ textAlign: "center", padding: "14px", background: "#C9A96E11", borderRadius: 8, border: "1px solid #C9A96E22" }}>
                  <div style={{ fontSize: 30, fontWeight: 700, color: "#C9A96E", fontFamily: "sans-serif" }}>6–7%</div>
                  <div style={{ fontSize: 10, color: "#888", letterSpacing: "0.15em", fontFamily: "sans-serif" }}>COMMISSION RATE</div>
                  <div style={{ fontSize: 10, color: "#C9A96E", fontFamily: "sans-serif", marginTop: 5 }}>Tiered slabs to reward performance</div>
                </div>
                <div style={{ textAlign: "center", padding: "14px", background: "#1a4a1a22", borderRadius: 8, border: "1px solid #2a6a2a33" }}>
                  <div style={{ fontSize: 30, fontWeight: 700, color: "#5cb85c", fontFamily: "sans-serif" }}>&lt;7 days</div>
                  <div style={{ fontSize: 10, color: "#888", letterSpacing: "0.15em", fontFamily: "sans-serif" }}>PAYOUT SPEED</div>
                  <div style={{ fontSize: 10, color: "#5cb85c", fontFamily: "sans-serif", marginTop: 5 }}>Both tranches paid fast</div>
                </div>
              </div>
              <div style={{ borderTop: "1px solid #222", paddingTop: 18 }}>
                <div style={{ fontSize: 11, color: "#888", letterSpacing: "0.12em", fontFamily: "sans-serif", marginBottom: 12 }}>COMMISSION PAYOUT SCHEDULE</div>
                <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
                  {[
                    { step: "1st", trigger: "Client pays 10% + SPA is issued", detail: "1st half of commission paid within 7 days", color: "#C9A96E" },
                    { step: "2nd", trigger: "Client completes 15% total payment", detail: "2nd half of commission paid within 7 days", color: "#5cb85c" },
                  ].map(s => (
                    <div key={s.step} style={{ display: "flex", gap: 14, alignItems: "flex-start", background: "#111", borderRadius: 8, padding: "12px 16px", border: `1px solid ${s.color}22` }}>
                      <div style={{ width: 30, height: 30, borderRadius: "50%", background: s.color + "22", border: `2px solid ${s.color}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 10, fontWeight: 700, color: s.color, fontFamily: "sans-serif", flexShrink: 0 }}>{s.step}</div>
                      <div>
                        <div style={{ fontSize: 12, color: "#ddd", fontFamily: "sans-serif", marginBottom: 2 }}><strong>Trigger:</strong> {s.trigger}</div>
                        <div style={{ fontSize: 11, color: s.color, fontFamily: "sans-serif", fontStyle: "italic" }}>✓ {s.detail}</div>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            </div>
          </div>
        )}

        {/* Footer */}
        <div style={{ marginTop: 40, padding: "20px", background: "#0d0d0d", borderRadius: 8, border: "1px solid #222", textAlign: "center" }}>
          <div style={{ fontSize: 10, letterSpacing: "0.25em", color: "#555", fontFamily: "sans-serif", marginBottom: 6 }}>DEVELOPED BY</div>
          <div style={{ fontSize: 16, color: "#C9A96E", letterSpacing: "0.1em" }}>ATARA Development</div>
          <div style={{ fontSize: 10, color: "#444", fontFamily: "sans-serif", marginTop: 5 }}>The Residences at Sheraton Al Marjan Island · Treasure Island · Ras Al Khaimah · UAE</div>
          <div style={{ fontSize: 9, color: "#2a2a2a", fontFamily: "sans-serif", marginTop: 10 }}>This document is prepared for broker and investor use. All details subject to terms and conditions.</div>
        </div>
      </div>
    </div>
  );
}
