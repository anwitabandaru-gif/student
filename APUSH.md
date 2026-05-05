---
permalink: /apush
---

<html lang="en">
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>APUSH Comprehensive Timeline</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Source+Serif+4:ital,wght@0,300;0,400;0,600;1,300&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0f0e0b;
    --bg2: #18160f;
    --bg3: #221f15;
    --gold: #c9a84c;
    --gold2: #e8c96a;
    --cream: #f0e6c8;
    --muted: #9a8d6e;
    --border: #2e2a1e;
    --border2: #3e3826;

    --fp: #2563a8;
    --fp-bg: #0d1e35;
    --fp-text: #7ab3e8;

    --ec: #1a7a3e;
    --ec-bg: #0a2015;
    --ec-text: #6fc98a;

    --na: #8a5c1a;
    --na-bg: #241808;
    --na-text: #d4924a;

    --wo: #8a2060;
    --wo-bg: #28091c;
    --wo-text: #d47ab0;

    --ct: #5a2e9a;
    --ct-bg: #1a0d2e;
    --ct-text: #a87edc;

    --li: #1a7a7a;
    --li-bg: #082020;
    --li-text: #5ec8c8;

    --in: #7a3a10;
    --in-bg: #200e04;
    --in-text: #d48040;

    --re: #5a4e1a;
    --re-bg: #181408;
    --re-text: #c4b050;

    --im: #2a4e8a;
    --im-bg: #0c1828;
    --im-text: #6898d8;

    --cr: #8a1a1a;
    --cr-bg: #280808;
    --cr-text: #d46060;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--cream);
    font-family: 'Source Serif 4', Georgia, serif;
    min-height: 100vh;
    max-width: 1000px !important;
  }

  header {
    background: var(--bg2);
    border-bottom: 1px solid var(--gold);
    padding: 2rem 2rem 1.5rem;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  header h1 {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    font-weight: 900;
    color: var(--gold2);
    letter-spacing: 0.05em;
    text-transform: uppercase;
    margin-bottom: 0.75rem;
  }

  .controls {
    display: flex;
    gap: 0.75rem;
    flex-wrap: wrap;
    align-items: center;
  }

  .search-wrap {
    position: relative;
    flex: 1;
    min-width: 200px;
    max-width: 320px;
  }

  .search-wrap input {
    width: 100%;
    background: var(--bg3);
    border: 1px solid var(--border2);
    color: var(--cream);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    padding: 0.45rem 0.75rem;
    border-radius: 4px;
    outline: none;
  }

  .search-wrap input:focus { border-color: var(--gold); }
  .search-wrap input::placeholder { color: var(--muted); }

  .era-select {
    background: var(--bg3);
    border: 1px solid var(--border2);
    color: var(--cream);
    font-family: 'Source Serif 4', serif;
    font-size: 0.8rem;
    padding: 0.45rem 0.75rem;
    border-radius: 4px;
    outline: none;
    cursor: pointer;
  }

  .era-select:focus { border-color: var(--gold); }

  .cat-filters {
    display: flex;
    gap: 0.4rem;
    flex-wrap: wrap;
  }

  .cat-btn {
    font-size: 0.68rem;
    font-family: 'JetBrains Mono', monospace;
    padding: 0.3rem 0.6rem;
    border-radius: 3px;
    border: 1px solid transparent;
    cursor: pointer;
    transition: opacity 0.15s;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .cat-btn.active { opacity: 1; }
  .cat-btn.inactive { opacity: 0.35; }

  .cat-btn.fp  { background: var(--fp-bg);  color: var(--fp-text);  border-color: var(--fp); }
  .cat-btn.ec  { background: var(--ec-bg);  color: var(--ec-text);  border-color: var(--ec); }
  .cat-btn.na  { background: var(--na-bg);  color: var(--na-text);  border-color: var(--na); }
  .cat-btn.wo  { background: var(--wo-bg);  color: var(--wo-text);  border-color: var(--wo); }
  .cat-btn.ct  { background: var(--ct-bg);  color: var(--ct-text);  border-color: var(--ct); }
  .cat-btn.li  { background: var(--li-bg);  color: var(--li-text);  border-color: var(--li); }
  .cat-btn.in  { background: var(--in-bg);  color: var(--in-text);  border-color: var(--in); }
  .cat-btn.re  { background: var(--re-bg);  color: var(--re-text);  border-color: var(--re); }
  .cat-btn.im  { background: var(--im-bg);  color: var(--im-text);  border-color: var(--im); }
  .cat-btn.cr  { background: var(--cr-bg);  color: var(--cr-text);  border-color: var(--cr); }

  .counter {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--muted);
    margin-left: auto;
    white-space: nowrap;
  }

  .timeline-wrap {
    max-width: 900px;
    margin: 0 auto;
    padding: 2rem 1.5rem 4rem;
  }

  .era-block {
    margin-bottom: 3rem;
  }

  .era-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1.25rem;
    padding-bottom: 0.5rem;
    border-bottom: 1px solid var(--border2);
  }

  .era-num {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    font-weight: 900;
    color: var(--gold);
    line-height: 1;
    min-width: 2.5rem;
  }

  .era-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--gold2);
    letter-spacing: 0.03em;
  }

  .era-years {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--muted);
    margin-top: 0.1rem;
  }

  .events-list {
    display: flex;
    flex-direction: column;
    gap: 0;
    position: relative;
    padding-left: 2rem;
  }

  .events-list::before {
    content: '';
    position: absolute;
    left: 0.45rem;
    top: 0.5rem;
    bottom: 0.5rem;
    width: 1px;
    background: linear-gradient(to bottom, var(--gold), var(--border2));
  }

  .event-item {
    position: relative;
    padding: 0.6rem 0.75rem 0.6rem 0;
    border-bottom: 1px solid var(--border);
    cursor: pointer;
    transition: background 0.1s;
  }

  .event-item:last-child { border-bottom: none; }
  .event-item:hover { background: var(--bg2); border-radius: 4px; }

  .event-item::before {
    content: '';
    position: absolute;
    left: -1.6rem;
    top: 1rem;
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--gold);
    border: 1px solid var(--bg);
  }

  .event-top {
    display: flex;
    align-items: baseline;
    gap: 0.75rem;
    flex-wrap: wrap;
  }

  .event-year {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: var(--gold);
    white-space: nowrap;
    min-width: 80px;
    font-weight: 500;
  }

  .event-title {
    font-family: 'Playfair Display', serif;
    font-size: 0.95rem;
    font-weight: 700;
    color: var(--cream);
    flex: 1;
  }

  .event-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.62rem;
    padding: 0.15rem 0.45rem;
    border-radius: 3px;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    white-space: nowrap;
  }

  .event-tag.fp  { background: var(--fp-bg);  color: var(--fp-text); }
  .event-tag.ec  { background: var(--ec-bg);  color: var(--ec-text); }
  .event-tag.na  { background: var(--na-bg);  color: var(--na-text); }
  .event-tag.wo  { background: var(--wo-bg);  color: var(--wo-text); }
  .event-tag.ct  { background: var(--ct-bg);  color: var(--ct-text); }
  .event-tag.li  { background: var(--li-bg);  color: var(--li-text); }
  .event-tag.in  { background: var(--in-bg);  color: var(--in-text); }
  .event-tag.re  { background: var(--re-bg);  color: var(--re-text); }
  .event-tag.im  { background: var(--im-bg);  color: var(--im-text); }
  .event-tag.cr  { background: var(--cr-bg);  color: var(--cr-text); }

  .event-desc {
    font-size: 0.82rem;
    color: var(--muted);
    line-height: 1.55;
    margin-top: 0.3rem;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.25s ease;
  }

  .event-item.open .event-desc {
    max-height: 200px;
  }

  .no-results {
    text-align: center;
    padding: 3rem;
    color: var(--muted);
    font-style: italic;
  }

  .hidden { display: none !important; }
</style>


<header>
  <h1>APUSH Comprehensive Timeline</h1>
  <div class="controls">
    <div class="search-wrap">
      <input type="text" id="search" placeholder="Search events...">
    </div>
    <select class="era-select" id="eraFilter">
      <option value="all">All Eras</option>
      <option value="1">1 · Age of Exploration</option>
      <option value="2">2 · Colonial Era</option>
      <option value="3">3 · Revolutionary Era</option>
      <option value="4">4 · Early Republic</option>
      <option value="5">5 · Jacksonian Era</option>
      <option value="6">6 · Antebellum / Civil War</option>
      <option value="7">7 · Gilded Age</option>
      <option value="8">8 · Progressive Era</option>
      <option value="9">9 · Interwar Period</option>
      <option value="10">10 · World War II</option>
      <option value="11">11 · Cold War</option>
      <option value="12">12 · Modern Era</option>
    </select>
    <span class="counter" id="counter">0 events</span>
  </div>
  <div class="cat-filters" style="margin-top:0.6rem;">
    <button class="cat-btn fp active" data-cat="fp">Foreign Policy</button>
    <button class="cat-btn ec active" data-cat="ec">Economics</button>
    <button class="cat-btn na active" data-cat="na">Native Americans</button>
    <button class="cat-btn wo active" data-cat="wo">Women</button>
    <button class="cat-btn ct active" data-cat="ct">Court Cases</button>
    <button class="cat-btn li active" data-cat="li">Literature</button>
    <button class="cat-btn in active" data-cat="in">Innovations</button>
    <button class="cat-btn re active" data-cat="re">Religion/Ed</button>
    <button class="cat-btn im active" data-cat="im">Immigration</button>
    <button class="cat-btn cr active" data-cat="cr">Civil Rights</button>
  </div>
</header>

<div class="timeline-wrap" id="timelineWrap"></div>

<script>
const ERAS = [
  { num:1,  title:"Age of Exploration",    years:"1491–1607" },
  { num:2,  title:"Colonial Era",           years:"1607–1754" },
  { num:3,  title:"Revolutionary Era",      years:"1754–1800" },
  { num:4,  title:"Early Republic",         years:"1800–1828" },
  { num:5,  title:"Jacksonian Era",         years:"1828–1848" },
  { num:6,  title:"Antebellum / Civil War", years:"1848–1877" },
  { num:7,  title:"Gilded Age",             years:"1865–1898" },
  { num:8,  title:"Progressive Era",        years:"1890–1920" },
  { num:9,  title:"Interwar Period",        years:"1920–1941" },
  { num:10, title:"World War II",           years:"1941–1945" },
  { num:11, title:"Cold War",               years:"1945–1980" },
  { num:12, title:"Modern Era",             years:"1980–present" }
];

const CAT_LABELS = {
  fp:"Foreign Policy", ec:"Economics", na:"Native Americans",
  wo:"Women", ct:"Court Cases", li:"Literature/Culture",
  in:"Innovations", re:"Religion/Education", im:"Immigration", cr:"Civil Rights"
};

const EVENTS = [
  // Era 1 - Age of Exploration
  {yr:1400, yd:"c. 1400s", e:"Three Sisters Farming", d:"Native American technique of growing corn, beans, and squash together — more efficient and sustainable.", c:"na", era:1},
  {yr:1492, yd:"1492", e:"Columbus Arrives in the Americas", d:"Columbus lands in the Caribbean while sailing for Spain, beginning long-term European colonization and interaction with Native Americans.", c:"fp", era:1},
  {yr:1494, yd:"1494", e:"Treaty of Tordesillas", d:"Spain and Portugal divide newly discovered lands along a line in the Atlantic, giving Spain most of the Americas.", c:"fp", era:1},
  {yr:1503, yd:"1503", e:"Encomienda System", d:"Spain creates a labor system forcing Native Americans to work in exchange for supposed protection and Christian conversion.", c:"na", era:1},
  {yr:1517, yd:"1517", e:"Protestant Reformation", d:"Martin Luther rejects the Catholic Church, leading to creation of Protestant churches — reshaping European religious identity before colonization.", c:"re", era:1},
  {yr:1550, yd:"1550", e:"Valladolid Debate", d:"Spanish leaders debate whether Native Americans should be treated as equals or exploited — an early discussion of human rights.", c:"na", era:1},
  {yr:1570, yd:"1570", e:"Powhatan Confederacy Formed", d:"Multiple Native tribes in Virginia unite under Chief Powhatan to strengthen political power and defend their land.", c:"na", era:1},

  // Era 2 - Colonial
  {yr:1607, yd:"1607", e:"Founding of Jamestown", d:"England establishes its first permanent colony. Initially unstable — survived with help from Native Americans, tobacco farming, and eventually the arrival of women.", c:"im", era:2},
  {yr:1610, yd:"1610–1614", e:"1st Anglo-Powhatan War", d:"Fighting between English settlers and the Powhatan Confederacy over land and resources, ending in temporary peace.", c:"na", era:2},
  {yr:1618, yd:"1618", e:"Headright System", d:"Virginia and Maryland reward anyone who paid for an indentured servant's passage with land, spurring colonial immigration.", c:"im", era:2},
  {yr:1619, yd:"1619", e:"First Africans Arrive in Virginia", d:"African women and men arrive, forced into labor. Laws later made children inherit their mother's enslaved status — making women's reproduction central to slavery's growth.", c:"wo", era:2},
  {yr:1620, yd:"1620", e:"Mayflower / Plymouth Colony", d:"Puritan pilgrims establish Plymouth Colony to escape religious persecution. The Mayflower Compact establishes self-governance principles.", c:"re", era:2},
  {yr:1637, yd:"1637", e:"Anne Hutchinson Banished", d:"A woman who publicly challenged male religious authority is exiled, illustrating colonial society's strict limits on female independence.", c:"wo", era:2},
  {yr:1637, yd:"1637", e:"Pequot War", d:"English settlers and Native allies nearly wipe out the Pequot tribe in New England, establishing a pattern of violent colonial expansion.", c:"na", era:2},
  {yr:1637, yd:"1637", e:"Harvard Founded", d:"First institution of higher learning established in the American colonies, in Cambridge, Massachusetts.", c:"re", era:2},
  {yr:1644, yd:"1644–1646", e:"2nd Anglo-Powhatan War", d:"English settlers further expand into Virginia, weakening Native resistance in the region.", c:"na", era:2},
  {yr:1649, yd:"1649", e:"Maryland Act of Toleration", d:"Mandates religious tolerance for Trinitarian Christians — an early model for the First Amendment's freedom of religion clause.", c:"re", era:2},
  {yr:1651, yd:"1651–1696", e:"Navigation Laws", d:"Series of laws regulating colonial shipping — only English ships could trade in English/colonial ports, tying colonies to mercantile system.", c:"ec", era:2},
  {yr:1662, yd:"1662", e:"Virginia Hereditary Slave Law", d:"A child's slavery status follows the mother, making enslaved women's reproduction the engine of slavery's expansion.", c:"wo", era:2},
  {yr:1662, yd:"1662", e:"Halfway Covenant", d:"Partial church membership for New England Puritans to address declining church membership — a sign of weakening Puritan grip on colonial life.", c:"re", era:2},
  {yr:1675, yd:"1675–1676", e:"King Philip's War", d:"Deadliest colonial war — led by Metacom (King Philip), Native Americans fight English settlers but are ultimately defeated, losing vast amounts of land.", c:"na", era:2},
  {yr:1676, yd:"1676", e:"Bacon's Rebellion", d:"Frontier settlers (many former indentured servants) rebel against Virginia's government over Native policy, exposing class tensions. Accelerated the shift to African slavery.", c:"im", era:2},
  {yr:1680, yd:"1680", e:"Pueblo Revolt", d:"Pueblo people successfully revolt against Spanish rule, driving them out of New Mexico for over a decade.", c:"na", era:2},
  {yr:1689, yd:"1689", e:"Locke's Second Treatise of Government", d:"Discusses natural rights of 'Life, Liberty, Property' — foundational text for American revolutionary thinking.", c:"li", era:2},
  {yr:1692, yd:"1692", e:"Salem Witch Trials", d:"Trials disproportionately targeted women, showing how colonial society punished those who stepped outside traditional roles.", c:"wo", era:2},
  {yr:1715, yd:"1715–1717", e:"Yamasee War", d:"Native tribes in the Southeast fight British colonists over unfair trade and land loss, nearly destroying South Carolina.", c:"na", era:2},
  {yr:1730, yd:"1730s–1740s", e:"First Great Awakening", d:"Series of Protestant revivals characterized by emotional preaching (Jonathan Edwards, George Whitefield). Gave women a larger role in religious life.", c:"re", era:2},
  {yr:1735, yd:"1735", e:"Zenger Trial", d:"John Peter Zenger acquitted of seditious libel — truthful criticism of the government is not libel. Early freedom of the press ruling.", c:"ct", era:2},
  {yr:1737, yd:"1737", e:"Walking Purchase", d:"Pennsylvania colonists trick the Lenape into giving up more land than agreed by manipulating a land 'walk' agreement.", c:"na", era:2},
  {yr:1750, yd:"1650–1776", e:"Mercantilism", d:"Dominant economic theory linking political power to gold/silver reserves. Britain taxed and regulated colonies to maximize home country wealth.", c:"ec", era:2},

  // Era 3 - Revolutionary
  {yr:1754, yd:"1754", e:"Albany Congress", d:"7 colonies meet with Iroquois leaders to create a defense alliance against France — early experiment in inter-colonial cooperation.", c:"fp", era:3},
  {yr:1754, yd:"1754–1763", e:"French and Indian War", d:"Britain defeats France and Native allies in the Seven Years' War, gaining control of the Ohio River Valley and all of North America east of the Mississippi.", c:"fp", era:3},
  {yr:1763, yd:"1763", e:"Treaty of Paris (1763)", d:"Formally ends the Seven Years' War. France cedes almost all North American territory to Britain. France loses colonial power in the New World.", c:"fp", era:3},
  {yr:1763, yd:"1763–1765", e:"Pontiac's Rebellion", d:"Native American uprising against Britain in the Ohio Valley. Ended partly because Natives ran low on supplies and could not capture major forts.", c:"na", era:3},
  {yr:1763, yd:"1763", e:"Proclamation of 1763", d:"Britain forbids colonial settlement west of the Appalachians after Pontiac's Rebellion — recognizes Native land rights and angers colonists.", c:"na", era:3},
  {yr:1764, yd:"1764", e:"Sugar Act", d:"First tax imposed on colonists by the crown — duty on imported sugar from West Indies. Lowered after protests.", c:"ec", era:3},
  {yr:1765, yd:"1765", e:"Stamp Act", d:"Widely unpopular tax on paper goods, repealed 1766 after mass colonial protests.", c:"ec", era:3},
  {yr:1765, yd:"1765", e:"Daughters of Liberty / Stamp Act Protests", d:"Women organized by the Daughters of Liberty boycotted British goods and produced homemade goods, playing a key role in colonial resistance.", c:"wo", era:3},
  {yr:1767, yd:"1767", e:"Townshend Acts", d:"Taxes on glass, lead, paper, paint, and tea used to pay colonial governors — seen as circumventing colonial assemblies and sparking further outrage.", c:"ec", era:3},
  {yr:1770, yd:"1770s", e:"Republican Motherhood", d:"Emerging ideology that women's role was to raise patriotic sons — limited but acknowledged women's civic importance.", c:"wo", era:3},
  {yr:1776, yd:"1776", e:"Common Sense (Thomas Paine)", d:"Convinced American colonists that full independence was the best solution, using passionate, simple language to reach ordinary people.", c:"li", era:3},
  {yr:1776, yd:"1776", e:"Declaration of Independence", d:"Declares independence from Britain, grounded in Enlightenment ideals of natural rights. Abigail Adams urged lawmakers to 'Remember the Ladies,' largely ignored.", c:"cr", era:3},
  {yr:1776, yd:"1776", e:"Abigail Adams Writes 'Remember the Ladies'", d:"Urged lawmakers to consider women's rights in the new nation — an early articulation of gender inequality.", c:"wo", era:3},
  {yr:1778, yd:"1778", e:"Franco-American Alliance", d:"French military and financial support for the Patriots, negotiated by Ben Franklin. Critical to American victory in the Revolution.", c:"fp", era:3},
  {yr:1781, yd:"1781", e:"Articles of Confederation Ratified", d:"First U.S. governing document — created a weak central government with no power to tax. Led to economic instability and the Constitution.", c:"ec", era:3},
  {yr:1783, yd:"1783", e:"Treaty of Paris (1783)", d:"Ends the American Revolution. Britain recognizes U.S. independence and grants trans-Appalachian territory.", c:"fp", era:3},
  {yr:1786, yd:"1786–1787", e:"Shays' Rebellion", d:"Massachusetts farmers revolt against debt collection and high taxes under the Articles of Confederation — reveals the need for a stronger federal government.", c:"ec", era:3},
  {yr:1787, yd:"1787", e:"Constitutional Convention", d:"Produces the U.S. Constitution, featuring checks and balances, bicameralism, federalism, and the compromise of slavery (3/5 Compromise).", c:"ct", era:3},
  {yr:1787, yd:"1787–1788", e:"The Federalist Papers", d:"Hamilton, Madison, Jay write essays persuading New York to ratify the Constitution, advocating for a strong federal government.", c:"li", era:3},
  {yr:1789, yd:"1789", e:"Judiciary Act of 1789", d:"Established the federal court structure including the Supreme Court with one chief justice and five associates.", c:"ct", era:3},
  {yr:1790, yd:"1790–1791", e:"Hamilton's Economic Plan", d:"Federal assumption of state debts; creation of the Bank of the U.S.; protective tariffs and subsidies for industry; excise taxes.", c:"ec", era:3},
  {yr:1790, yd:"1790", e:"Judith Sargent Murray — On Equality of the Sexes", d:"Argued women are intellectually equal to men and deserve education — one of the first clear statements of gender equality in early America.", c:"wo", era:3},
  {yr:1790, yd:"1790s–1840s", e:"French and Irish Immigration / Alien & Sedition Acts", d:"Anti-immigrant laws raising residency requirements and giving the president power to deport 'dangerous' aliens, aimed at pro-Jeffersonian European immigrants.", c:"im", era:3},
  {yr:1791, yd:"1791", e:"Bill of Rights Ratified", d:"First 10 amendments guarantee individual freedoms including free speech, religion, press, and due process.", c:"cr", era:3},
  {yr:1791, yd:"1791", e:"Bank of the United States", d:"Chartered by Congress as part of Hamilton's plan. Printed paper money and served as a depository for Treasury funds.", c:"ec", era:3},
  {yr:1793, yd:"1793", e:"Neutrality Proclamation (Washington)", d:"Washington declares U.S. neutrality in the wars following the French Revolution. Sets the tone for 100+ years of American isolationism.", c:"fp", era:3},
  {yr:1793, yd:"1793", e:"Cotton Gin (Eli Whitney)", d:"Removes cotton seeds 50x faster than manual labor — made cotton massively profitable and dramatically increased the demand for enslaved labor.", c:"in", era:3},
  {yr:1793, yd:"1793", e:"Textile Mill (Samuel Slater)", d:"Water-powered textile mill in New England begins the American factory system.", c:"in", era:3},
  {yr:1794, yd:"1794", e:"Jay's Treaty", d:"Chief Justice Jay negotiates trade normalization with Britain and British troop withdrawal from Appalachian Territory.", c:"fp", era:3},
  {yr:1794, yd:"1794", e:"Whiskey Rebellion", d:"Pennsylvania distillers revolt against Hamilton's excise tax on whiskey. Washington crushes it with militia — establishes federal authority.", c:"ec", era:3},
  {yr:1794, yd:"1794", e:"Battle of Fallen Timbers", d:"Gen. 'Mad' Anthony Wayne defeats a Native American confederacy. Tribes forced to sign the Treaty of Greenville.", c:"na", era:3},
  {yr:1795, yd:"1795", e:"Pinkney's Treaty", d:"Spain grants the U.S. navigation of the Mississippi River and duty-free transport through the port of New Orleans.", c:"fp", era:3},
  {yr:1795, yd:"1795", e:"Treaty of Greenville", d:"Natives forced to cede southern/eastern Ohio and parts of Michigan, Indiana, and Illinois. U.S. pays $20,000 in goods.", c:"na", era:3},
  {yr:1796, yd:"1796", e:"Washington's Farewell Address", d:"Washington warns against binding military alliances and political factions — fuels decades of American isolationism.", c:"fp", era:3},
  {yr:1796, yd:"1796", e:"Hylton v. United States", d:"First Supreme Court case to rule on a federal tax's constitutionality. Ruled luxury taxes are indirect, not direct taxes.", c:"ct", era:3},
  {yr:1797, yd:"1797", e:"XYZ Affair", d:"French demand bribes from U.S. diplomats to negotiate, sparking outrage and leading to an undeclared Quasi-War.", c:"fp", era:3},
  {yr:1798, yd:"1798–1800", e:"Quasi-War with France", d:"Undeclared naval war in the Caribbean between the U.S. and France following the XYZ Affair.", c:"fp", era:3},
  {yr:1798, yd:"1798", e:"Alien and Sedition Acts", d:"Raised residency requirements for citizenship; allowed deportation of dangerous aliens; restricted speech critical of government.", c:"cr", era:3},

  // Era 4 - Early Republic
  {yr:1800, yd:"1800", e:"Convention of 1800", d:"Ended the Quasi-War and the Franco-American Alliance, normalizing U.S.–France relations.", c:"fp", era:4},
  {yr:1800, yd:"1800s", e:"Second Great Awakening", d:"Protestant religious revival encouraging moral reform — fueled the abolition movement and women's rights activism.", c:"re", era:4},
  {yr:1801, yd:"1801", e:"1st Barbary War", d:"Jefferson dispatched the U.S. Navy because the U.S. refused to pay tributes for piracy protection — first foreign war.", c:"fp", era:4},
  {yr:1801, yd:"1801", e:"Judiciary Act of 1801 (Midnight Judges)", d:"Federalists attempt to retain judicial power after losing the 1800 election — adds 16 new federal judges and reduces the Supreme Court.", c:"ct", era:4},
  {yr:1801, yd:"1801", e:"Interchangeable Parts (Eli Whitney)", d:"Standardized parts for musket production — enabled mass production and laid groundwork for the Industrial Revolution.", c:"in", era:4},
  {yr:1803, yd:"1803", e:"Marbury v. Madison", d:"Chief Justice Marshall establishes judicial review — the Supreme Court's power to declare laws unconstitutional. Landmark expansion of judicial power.", c:"ct", era:4},
  {yr:1803, yd:"1803", e:"Louisiana Purchase", d:"Napoleon sells the Louisiana Territory for $15 million (negotiated by Livingston and Monroe), doubling the size of the U.S.", c:"fp", era:4},
  {yr:1807, yd:"1807", e:"Embargo Act", d:"Closed U.S. ports to all exports — designed to enforce neutrality but severely damaged the American economy.", c:"fp", era:4},
  {yr:1807, yd:"1807", e:"Steamboat (Robert Fulton)", d:"Revolutionizes river transport by enabling upstream travel — makes rivers two-way and opens up interior trade.", c:"in", era:4},
  {yr:1809, yd:"1809", e:"Non-Intercourse Act", d:"Replaced the Embargo Act — reopened trade with all nations except Britain and France.", c:"fp", era:4},
  {yr:1810, yd:"1810", e:"Fletcher v. Peck", d:"First time the Supreme Court struck down a state law as unconstitutional — contracts protected under federal law.", c:"ct", era:4},
  {yr:1810, yd:"1810", e:"Macon's Bill No. 2", d:"U.S. would trade with whichever nation (Britain or France) first agreed to repeal commerce restrictions against America.", c:"ec", era:4},
  {yr:1811, yd:"1811", e:"Battle of Tippecanoe", d:"William Henry Harrison defeats a Native American confederacy under Tenskwatawa, caused by colonist expansion into Native territories.", c:"na", era:4},
  {yr:1812, yd:"1812–1815", e:"War of 1812", d:"Caused by British impressment of American sailors and British support for Native American resistance. Ended with the Treaty of Ghent.", c:"fp", era:4},
  {yr:1814, yd:"1814", e:"Treaty of Ghent", d:"Ends the War of 1812, returning all captured land and ships. Leads to the 'Era of Good Feelings.'", c:"fp", era:4},
  {yr:1815, yd:"1815–1824", e:"American System (Henry Clay)", d:"Three-part plan: strong banking system, protective tariff, and a federally funded transportation network.", c:"ec", era:4},
  {yr:1816, yd:"1816", e:"Tariff of 1816", d:"First protective tariff in American history — shielded New England manufacturers from British goods after the War of 1812.", c:"ec", era:4},
  {yr:1818, yd:"1818", e:"Rush-Bagot & Convention of 1818", d:"Demilitarizes the U.S.–Canadian Great Lakes border. U.S. and Britain agree on the 49th parallel and joint occupation of Oregon.", c:"fp", era:4},
  {yr:1819, yd:"1819", e:"Adams-Onis Treaty", d:"Spain cedes Florida to the U.S. in exchange for the U.S. renouncing its Texas claim.", c:"fp", era:4},
  {yr:1819, yd:"1819", e:"McCulloch v. Maryland", d:"Ruling: Bank of the U.S. is constitutional and states cannot tax federal institutions — expands federal power via implied powers.", c:"ct", era:4},
  {yr:1819, yd:"1819–1821", e:"Panic of 1819", d:"Severe financial crisis caused by the Bank of the U.S. tightening credit on western land purchases. Fueled Jacksonian democracy ideas.", c:"ec", era:4},
  {yr:1820, yd:"1820", e:"Missouri Compromise", d:"Missouri enters as a slave state, Maine as free. Slavery banned north of 36°30' line — temporarily resolves sectional crisis.", c:"cr", era:4},
  {yr:1820, yd:"1820s", e:"Cult of Domesticity", d:"Ideology holding women should be pious, pure, and confined to the home — limiting public roles but giving women moral authority used later by reformers.", c:"wo", era:4},
  {yr:1821, yd:"1821", e:"Cohens v. Virginia", d:"Supreme Court gains power to review validity of state court decisions — further centralizes federal judicial authority.", c:"ct", era:4},
  {yr:1823, yd:"1823", e:"Monroe Doctrine", d:"Closed the Western Hemisphere to new European colonization — foundational statement of American hemispheric supremacy.", c:"fp", era:4},
  {yr:1824, yd:"1824", e:"Gibbons v. Ogden", d:"Congress, not states, regulates interstate commerce. Strikes down NY's attempt to monopolize river trade.", c:"ct", era:4},
  {yr:1825, yd:"1825", e:"Erie Canal", d:"Connects the Great Lakes to the Hudson River, enabling growth of the Midwest and faster East–West trade.", c:"in", era:4},
  {yr:1826, yd:"1826", e:"Lowell System", d:"Factory model in Massachusetts employing young rural women in textile mills — one of the first large-scale entries of women into the industrial workforce.", c:"wo", era:4},
  {yr:1828, yd:"1828", e:"Tariff of Abominations", d:"Highly protective tariff hurting Southern consumers — deepens the sectional divide and triggers the Nullification Crisis.", c:"ec", era:4},

  // Era 5 - Jacksonian
  {yr:1830, yd:"1830", e:"Indian Removal Act", d:"Forced relocation of Native tribes eastward — ~100M acres of fertile land taken. Led directly to the Trail of Tears.", c:"na", era:5},
  {yr:1830, yd:"1830", e:"Book of Mormon Published", d:"Joseph Smith founds the Church of Jesus Christ of Latter-day Saints during the Second Great Awakening.", c:"re", era:5},
  {yr:1830, yd:"1830s–1860s", e:"Transcendentalism & Romanticism", d:"Emerson, Thoreau (Walden, Civil Disobedience), Poe, Hawthorne, Cooper. Emphasized individualism, emotion, nature, and self-reliance.", c:"li", era:5},
  {yr:1831, yd:"1831", e:"McCormick Reaper", d:"Horse-drawn mechanical grain harvester increases agricultural productivity, especially in the Midwest.", c:"in", era:5},
  {yr:1831, yd:"1831–1856", e:"The Liberator (William Lloyd Garrison)", d:"Northern abolitionist newspaper — one of the earliest voices in the organized abolition movement.", c:"li", era:5},
  {yr:1832, yd:"1832", e:"Bank War (Jackson vs. BUS)", d:"Jackson vetoes the recharter of the Bank of the U.S., calling it unconstitutional — transfers funds to state 'pet banks.'", c:"ec", era:5},
  {yr:1832, yd:"1832", e:"Nullification Crisis / Tariff of 1832", d:"South Carolina attempts to nullify federal tariffs. Jackson threatens force. Resolved by Compromise Tariff of 1833.", c:"ec", era:5},
  {yr:1832, yd:"1832", e:"Black Hawk War", d:"Conflict between the U.S. and Sauk/Fox tribes after Black Hawk crossed the Mississippi to reclaim Illinois land — resulted in U.S. victory.", c:"na", era:5},
  {yr:1832, yd:"1832", e:"Worcester v. Georgia", d:"Supreme Court ruled the Cherokee Nation is sovereign and Georgia laws do not apply on Cherokee land. Georgia ignored the ruling.", c:"ct", era:5},
  {yr:1833, yd:"1833", e:"Compromise Tariff of 1833", d:"Proposed by Henry Clay — reduced tariff rates from 1832 levels over 8 years, defusing the Nullification Crisis.", c:"ec", era:5},
  {yr:1837, yd:"1837", e:"Telegraph (Samuel Morse)", d:"Enables instant long-distance communication — transforms business and government.", c:"in", era:5},
  {yr:1837, yd:"1837", e:"Steel Plow (John Deere)", d:"Allows greater efficiency in tilling thick Midwestern soil, enabling agricultural expansion.", c:"in", era:5},
  {yr:1837, yd:"1837–1838", e:"Panic of 1837", d:"Caused by currency deflation, crop failure, foreign loan recalls, and the aftermath of the Bank War. Led to Van Buren's Divorce Bill.", c:"ec", era:5},
  {yr:1838, yd:"1838", e:"Trail of Tears", d:"Forced relocation of the Cherokee Nation to Oklahoma after Worcester v. Georgia ruling was ignored — thousands died.", c:"na", era:5},
  {yr:1840, yd:"1840–1860", e:"Realism in Literature", d:"Walt Whitman, Emily Dickinson — focused on common people, democracy, and everyday life.", c:"li", era:5},
  {yr:1841, yd:"1841", e:"Commonwealth v. Hunt", d:"Labor unions are ruled legal — a major victory for workers' right to organize.", c:"ct", era:5},
  {yr:1844, yd:"1844–1845", e:"Annexation of Texas", d:"Polk's expansionist policies led Congress, via joint resolution, to incorporate Texas into the Union.", c:"fp", era:5},
  {yr:1844, yd:"1844", e:"Treaty of Wanghia", d:"U.S. received the same open trade policies in China that Britain had negotiated.", c:"fp", era:5},
  {yr:1845, yd:"1845", e:"Narrative of Frederick Douglass", d:"Firsthand account of slavery by the former enslaved person turned abolitionist — disproved claims of 'Black inferiority.'", c:"li", era:5},
  {yr:1845, yd:"1845", e:"Irish Potato Famine / Immigration Wave", d:"Biological blight under British colonial rule pushes millions of Irish to emigrate — leading to anti-Catholic 'nativist' backlash and 'NINA' discrimination.", c:"im", era:5},
  {yr:1846, yd:"1846", e:"Mechanical Sewing Machine (Elias Howe)", d:"Stitches much faster than by hand, dramatically increasing productivity of textile and clothing industries.", c:"in", era:5},
  {yr:1846, yd:"1846", e:"Walker Tariff", d:"Part of Polk's plan — reduced average tariff rates from 32% to 25%, to the displeasure of Northern manufacturers.", c:"ec", era:5},
  {yr:1846, yd:"1846", e:"Oregon Treaty", d:"U.S. and Britain peacefully settle the Oregon Country boundary at the 49th parallel.", c:"fp", era:5},
  {yr:1846, yd:"1846–1848", e:"Mexican-American War", d:"U.S. declares war on Mexico over disputed Texas annexation boundary — Polk ordered troops to the Rio Grande to provoke conflict.", c:"fp", era:5},
  {yr:1848, yd:"1848", e:"Treaty of Guadalupe Hidalgo", d:"Grants the U.S. California, New Mexico, Arizona, Nevada, Utah, and Colorado — fulfills Manifest Destiny.", c:"fp", era:5},
  {yr:1848, yd:"1848", e:"Seneca Falls Convention", d:"First women's rights convention organized by Elizabeth Cady Stanton and Lucretia Mott — produced the Declaration of Sentiments demanding equal rights and suffrage.", c:"wo", era:5},
  {yr:1848, yd:"1848", e:"German Revolution Failures / German Immigration", d:"Political refugees flee to the U.S. after failed democratic uprisings. Most settled in Midwest farms and businesses.", c:"im", era:5},
  {yr:1848, yd:"1844", e:"Great Disappointment (Millerites)", d:"Jesus fails to return as predicted by William Miller — major shock to the Millerite movement.", c:"re", era:5},

  // Era 6 - Antebellum/Civil War
  {yr:1850, yd:"1850", e:"Compromise of 1850", d:"California enters as a free state; stricter Fugitive Slave Law; popular sovereignty for other new territories — temporary truce in sectional conflict.", c:"cr", era:6},
  {yr:1850, yd:"1850", e:"Clayton-Bulwer Treaty", d:"U.S. and Britain agree to joint control over any future Central American canal, preventing either from gaining exclusive dominance.", c:"fp", era:6},
  {yr:1851, yd:"1851", e:"'Ain't I a Woman?' (Sojourner Truth)", d:"Powerful speech connecting race and gender justice at the Women's Rights Convention — Black women deserved the same rights as white women and free men.", c:"wo", era:6},
  {yr:1852, yd:"1852", e:"Uncle Tom's Cabin (Harriet Beecher Stowe)", d:"Humanized the horrors of slavery for Northern readers, galvanizing public opinion against slavery and intensifying sectional tensions.", c:"li", era:6},
  {yr:1852, yd:"1852", e:"Massachusetts School Attendance Act", d:"First U.S. law requiring children to attend school, pushed by Horace Mann.", c:"re", era:6},
  {yr:1853, yd:"1853", e:"Gadsden Purchase", d:"U.S. buys southern Arizona and New Mexico from Mexico to secure a southern railroad route.", c:"fp", era:6},
  {yr:1853, yd:"1853–1854", e:"Treaty of Kanagawa", d:"Commodore Matthew Perry uses naval pressure to force Japan to open trade relations with the U.S., ending Japan's isolation.", c:"fp", era:6},
  {yr:1854, yd:"1854", e:"Kansas-Nebraska Act", d:"Repealed the Missouri Compromise, allowing popular sovereignty on slavery in new territories — sparked 'Bleeding Kansas' and the Republican Party.", c:"cr", era:6},
  {yr:1856, yd:"1856", e:"Bessemer Steel Process", d:"Cheap method to convert iron into steel — enables mass production and the eventual construction of transcontinental railroads.", c:"in", era:6},
  {yr:1857, yd:"1857", e:"Dred Scott v. Sandford", d:"Enslaved man Scott denied freedom — Supreme Court rules enslaved people are not protected by the federal government in any state, overriding the Missouri Compromise.", c:"ct", era:6},
  {yr:1857, yd:"1857", e:"Impending Crisis of the South (Hinton Helper)", d:"White Southerner argues slavery was holding the South back economically — banned in the South.", c:"li", era:6},
  {yr:1857, yd:"1857", e:"Panic of 1857", d:"Overspeculation, gold inflation, and excess grain production cause economic collapse. More severe in the North — worsened sectional tensions.", c:"ec", era:6},
  {yr:1860, yd:"1860s", e:"Greenbacks", d:"Paper currency issued during the Civil War, inadequately backed by gold — caused value fluctuations but helped fund the Union war effort.", c:"ec", era:6},
  {yr:1861, yd:"1861", e:"Dorothea Dix Becomes Superintendent of Nurses", d:"Recruited and organized thousands of women nurses for the Union — significantly expanded women's accepted roles in public life.", c:"wo", era:6},
  {yr:1861, yd:"1861", e:"Confederate Diplomacy / Trent Affair", d:"South attempted to win British/French recognition. U.S. nearly went to war with Britain after seizing Confederate diplomats from a British ship.", c:"fp", era:6},
  {yr:1861, yd:"1861–1865", e:"Harriet Tubman as Union Servicewoman", d:"Tubman served as nurse, spy, and scout — led the Combahee River Raid (1863) freeing 700+ enslaved people. First U.S. military operation planned and led by a woman.", c:"wo", era:6},
  {yr:1861, yd:"1861", e:"Morrill Land Grant Act", d:"Provided grants of federal land to states to finance land-grant colleges — expands higher education.", c:"re", era:6},
  {yr:1862, yd:"1862", e:"Homestead Act", d:"Sold 160 acres for $30 with the condition of living and cultivating the land — promoted westward expansion.", c:"ec", era:6},
  {yr:1862, yd:"1862", e:"Ironclad Warships", d:"Union USS Monitor fights CSS Virginia — durability shifts naval warfare away from wooden vessels.", c:"in", era:6},
  {yr:1862, yd:"1862", e:"National Banking System", d:"Network of banks issuing currency against government bonds — helped stabilize national currency for 50 years until the Federal Reserve.", c:"ec", era:6},
  {yr:1863, yd:"1863", e:"Emancipation Proclamation", d:"Lincoln declares enslaved people in Confederate states free — reframes the Civil War as a war for human freedom.", c:"cr", era:6},
  {yr:1863, yd:"1863", e:"New York Draft Riots", d:"Violent protests by working-class Irish men against what they saw as an unfair military draft — class and ethnic tensions explode.", c:"im", era:6},
  {yr:1864, yd:"1864", e:"Sand Creek Massacre", d:"U.S. Army massacres hundreds of Cheyenne and Arapaho people in Colorado — triggered by westward expansion.", c:"na", era:6},
  {yr:1865, yd:"1865", e:"13th Amendment", d:"Abolished slavery throughout the United States.", c:"cr", era:6},
  {yr:1865, yd:"1865", e:"Women Enter the Workforce (Civil War)", d:"Northern women took over men's factory jobs during the war — but lost these positions when men returned.", c:"wo", era:6},
  {yr:1865, yd:"1865", e:"French Intervention in Mexico", d:"France installs Maximilian as Emperor. After the Civil War, the U.S. invokes the Monroe Doctrine and pressures France to withdraw.", c:"fp", era:6},
  {yr:1866, yd:"1866", e:"Reconstruction Acts", d:"Placed Southern states under military rule; required new state constitutions and Black male suffrage before re-admission.", c:"cr", era:6},
  {yr:1867, yd:"1867", e:"Purchase of Alaska", d:"Secretary of State Seward buys Alaska from Russia for $7.2 million — mocked as 'Seward's Folly,' later proved strategically valuable.", c:"fp", era:6},
  {yr:1867, yd:"1867", e:"Annexation of Midway Islands", d:"U.S. claims the Midway Islands — early American expansion beyond the continent.", c:"fp", era:6},
  {yr:1868, yd:"1868", e:"14th Amendment", d:"Grants citizenship and equal protection to all persons born in the U.S. — foundational for decades of civil rights litigation.", c:"cr", era:6},
  {yr:1870, yd:"1870", e:"15th Amendment", d:"Prohibits denying the right to vote based on race, color, or previous condition of servitude.", c:"cr", era:6},
  {yr:1875, yd:"1875", e:"US v. Cruikshank", d:"After the Colfax Massacre, court rules federal government cannot punish individuals for civil rights violations — guts Reconstruction enforcement.", c:"ct", era:6},
  {yr:1877, yd:"1877", e:"Compromise of 1877", d:"Ends Reconstruction — Hayes becomes president; federal troops withdraw from the South, abandoning Black civil rights.", c:"cr", era:6},

  // Era 7 - Gilded Age
  {yr:1869, yd:"1869", e:"Transcontinental Railroad", d:"Connects east and west coasts in 7 days of travel. Accelerates westward expansion — also led to railroad monopolies and the Credit Mobilier scandal.", c:"in", era:7},
  {yr:1873, yd:"1873", e:"Panic of 1873", d:"One of the nation's largest banks files for bankruptcy amid overspeculation in railroads, mines, and factories — caused massive unemployment.", c:"ec", era:7},
  {yr:1874, yd:"1874", e:"Barbed Wire", d:"Cheap fencing to contain cattle in the Great Plains — ends the open range cattle drives and cowboy lifestyle.", c:"in", era:7},
  {yr:1875, yd:"1875", e:"Resumption Act of 1875", d:"Government pledges to withdraw greenbacks and use paper money backed by gold starting 1879.", c:"ec", era:7},
  {yr:1875, yd:"1875", e:"Civil Rights Cases of 1875 / US v. Cruikshank", d:"Supreme Court strikes down the Civil Rights Act of 1875 — ruled the 14th/13th amendments couldn't prohibit private discrimination, expanding Jim Crow.", c:"ct", era:7},
  {yr:1876, yd:"1876", e:"Battle of Little Bighorn (Custer's Last Stand)", d:"One of the most significant Native American victories against the U.S. — eventually led to harsher treatment and expansion of the reservation system.", c:"na", era:7},
  {yr:1876, yd:"1876", e:"Telephone (Alexander Graham Bell)", d:"Allows live voice transmission over wire, connecting households and businesses nationwide.", c:"in", era:7},
  {yr:1877, yd:"1877", e:"Nez Perce War", d:"The U.S. attempts to force the Nez Perce onto a reservation. Chief Joseph led his people toward Canada but was forced to surrender.", c:"na", era:7},
  {yr:1879, yd:"1879", e:"Carlisle Industrial Indian School", d:"Founded by Henry Pratt to assimilate Natives — 'Kill the Indian, Save the Man.' Served as a model for government-sponsored boarding schools.", c:"na", era:7},
  {yr:1880, yd:"1880", e:"Big Sister Policy (James Blaine)", d:"Policy to rally Latin American countries to open markets to American traders.", c:"fp", era:7},
  {yr:1881, yd:"1881", e:"Century of Dishonor (Helen Hunt Jackson)", d:"Argues the U.S. government repeatedly broke its promises to Native peoples — revealed the hypocrisy of U.S. Native policy.", c:"li", era:7},
  {yr:1881, yd:"1881", e:"Tuskegee Institute Founded", d:"Founded by Booker T. Washington to provide higher education to African Americans.", c:"re", era:7},
  {yr:1882, yd:"1882", e:"Chinese Exclusion Act", d:"Prohibited all future immigration from China — culmination of racial tensions with Irish workers competing for labor. First major ethnic immigration ban.", c:"im", era:7},
  {yr:1882, yd:"1882", e:"Electrical Power Station (Thomas Edison)", d:"Pearl Street Station in Manhattan enables widespread adoption of electricity.", c:"in", era:7},
  {yr:1883, yd:"1883", e:"Civil Rights Cases of 1883", d:"Supreme Court strikes down the Civil Rights Act of 1875 — prioritized states' rights, expanding segregation through businesses and social settings.", c:"ct", era:7},
  {yr:1884, yd:"1884", e:"Federal Government Outlaws Sun Dance", d:"Traditional Native religious practice banned as part of forced assimilation policy.", c:"na", era:7},
  {yr:1886, yd:"1886", e:"Wabash, St. Louis & Pacific RR v. Illinois", d:"States cannot regulate interstate railroad rates — leads directly to Congress creating the ICC in 1887.", c:"ct", era:7},
  {yr:1887, yd:"1887", e:"Dawes Act", d:"Replaced the reservation system — decreased Native territory by 90 million acres and forced cultural assimilation through mandatory farming.", c:"na", era:7},
  {yr:1887, yd:"1887", e:"Interstate Commerce Act (ICC)", d:"Prohibited railroad rebates and price discrimination — set up the Interstate Commerce Commission to regulate business.", c:"ec", era:7},
  {yr:1887, yd:"1887", e:"Samoan Crisis", d:"Naval standoff between the U.S., Germany, and Britain over control of the Samoan Islands.", c:"fp", era:7},
  {yr:1889, yd:"1889–1891", e:"Billion Dollar Congress", d:"Congress under Harrison spends over $1 billion in peacetime for the first time — veterans' pensions, naval expansion, silver purchases.", c:"ec", era:7},
  {yr:1890, yd:"1890", e:"Wounded Knee Massacre", d:"U.S. Army kills hundreds of Lakota Sioux at Wounded Knee Creek — ends the Ghost Dance Movement and major Native resistance.", c:"na", era:7},
  {yr:1890, yd:"1890", e:"Sherman Anti-Trust Act", d:"Forbade combinations in restraint of trade — initially ineffective, but set the basis for monopoly regulation.", c:"ec", era:7},
  {yr:1890, yd:"1890", e:"McKinley Tariff", d:"Boosted tariff rates to highest peacetime levels (48.4%) — hurt farmers and eventually influenced annexation of Hawaii.", c:"ec", era:7},
  {yr:1890, yd:"1890", e:"NAWSA Founded (Susan B. Anthony & Elizabeth Cady Stanton)", d:"National American Woman Suffrage Association formed in response to women's exclusion from the 15th Amendment.", c:"wo", era:7},
  {yr:1890, yd:"1890", e:"Settlement House Movement (Jane Addams / Hull House)", d:"Hull House in Chicago helped immigrants with education, healthcare, and daycare — model for Progressive-era social reform.", c:"wo", era:7},
  {yr:1893, yd:"1893", e:"Panic of 1893", d:"Worst depression of the 19th century. Overspeculation, overbuilding, and silver-backed money damaged foreign credit. JP Morgan bailed out the federal government.", c:"ec", era:7},
  {yr:1893, yd:"1893", e:"Overthrow of Queen Liliuokalani", d:"American businessmen and sugar planters overthrow the last sovereign monarch of Hawaii — first step toward annexation.", c:"fp", era:7},
  {yr:1895, yd:"1895", e:"Radio (Wireless Transmission)", d:"Enables mass communication — creates national cultural identity; later used for FDR's fireside chats and the Harlem Renaissance.", c:"in", era:7},
  {yr:1895, yd:"1895", e:"Plessy v. Ferguson", d:"Supreme Court establishes 'separate but equal' doctrine — makes segregation constitutional, enables Jim Crow laws across the South.", c:"ct", era:7},
  {yr:1897, yd:"1897", e:"Dingley Tariff", d:"Highest tariff rates in U.S. history at the time — passed under McKinley to further protect American industry.", c:"ec", era:7},
  {yr:1898, yd:"1898", e:"Spanish-American War", d:"Began with the sinking of the USS Maine. U.S. gains sovereignty over Puerto Rico, Guam, and the Philippines; establishes a protectorate over Cuba.", c:"fp", era:7},
  {yr:1898, yd:"1898", e:"Treaty of Paris (1898)", d:"Ends the Spanish-American War — U.S. gains Cuba, Puerto Rico, and Guam from Spain and buys the Philippines for $20 million.", c:"fp", era:7},
  {yr:1898, yd:"1898", e:"Anti-Imperialist League", d:"Organization established to battle American annexation of the Philippines — figures include Mark Twain and Andrew Carnegie.", c:"fp", era:7},
  {yr:1898, yd:"1898", e:"United States v. Wong Kim Ark", d:"Court rules people born in the U.S. are citizens even if parents are not — establishes birthright citizenship under the 14th Amendment.", c:"ct", era:7},

  // Era 8 - Progressive
  {yr:1899, yd:"1899–1902", e:"Philippine-American War", d:"After U.S. annexation of the Philippines, Filipino revolutionaries launched an insurgency against American rule. Ended when Emilio Aguinaldo was captured.", c:"fp", era:8},
  {yr:1900, yd:"1900", e:"Boxer Rebellion", d:"Uprising against foreigners in China, suppressed by an international force including the U.S. Strengthened the Open Door policy.", c:"fp", era:8},
  {yr:1900, yd:"1900", e:"Gold Standard Act", d:"Only gold could redeem paper currency, not silver — ended the currency debate in favor of 'sound money.'", c:"ec", era:8},
  {yr:1901, yd:"1901", e:"Insular Cases", d:"Court creates 'unincorporated territory' status — constitutional rights do not fully apply to the Philippines, Puerto Rico, and Guam.", c:"ct", era:8},
  {yr:1901, yd:"1901", e:"Platt Amendment", d:"Restricts Cuba's treaty-making powers, allows U.S. intervention, and requires Cuba to lease land for naval bases (Guantanamo Bay).", c:"fp", era:8},
  {yr:1901, yd:"1901", e:"Hay-Pauncefote Treaty", d:"Britain concedes U.S. rights to build the Panama Canal.", c:"fp", era:8},
  {yr:1902, yd:"1902", e:"Northern Securities Antitrust Case", d:"Roosevelt busts the Northwest railroad monopoly — upheld by the Supreme Court, signaling the Progressive Era's trust-busting approach.", c:"ec", era:8},
  {yr:1903, yd:"1903", e:"Airplane (Wright Brothers)", d:"First flight at Kitty Hawk — transforms travel, commerce, and warfare.", c:"in", era:8},
  {yr:1903, yd:"1903", e:"Elkins Act", d:"Fined railroads and those who accepted rebates — strengthened railroad regulation.", c:"ec", era:8},
  {yr:1904, yd:"1904", e:"Panama Canal", d:"After a failed French attempt, the U.S. begins construction to reduce travel time between Atlantic and Pacific — boosts trade and military strategy.", c:"fp", era:8},
  {yr:1904, yd:"1904", e:"Roosevelt Corollary", d:"Addition to the Monroe Doctrine — the U.S. will intervene in Latin America to maintain stability and prevent European intervention. 'Big Stick' diplomacy.", c:"fp", era:8},
  {yr:1905, yd:"1905", e:"Lochner v. New York", d:"Supreme Court strikes down New York's 10-hour bakery workday law — the 14th Amendment protects contracts, limiting labor regulation.", c:"ct", era:8},
  {yr:1905, yd:"1905", e:"Portsmouth Treaty", d:"Roosevelt mediates an end to the Russo-Japanese War — earns him the Nobel Peace Prize.", c:"fp", era:8},
  {yr:1906, yd:"1906", e:"The Jungle (Upton Sinclair)", d:"Exposes meatpacking working conditions — directly led to the Meat Inspection Act and the Pure Food and Drug Act.", c:"li", era:8},
  {yr:1906, yd:"1906", e:"Hepburn Act", d:"Expanded the ICC's power — restricted railroad free passes and bribes.", c:"ec", era:8},
  {yr:1907, yd:"1907", e:"Gentlemen's Agreement (U.S.–Japan)", d:"Japan restricts emigration to the U.S. while the U.S. avoids an official ban — reflects anti-Asian sentiment.", c:"im", era:8},
  {yr:1908, yd:"1908", e:"Muller v. Oregon", d:"Court upholds Oregon's 10-hour workday for women — because of women's role as mothers, the state may protect their health.", c:"ct", era:8},
  {yr:1908, yd:"1908", e:"Model T Automobile (Ford)", d:"First affordable mass consumer car — leads to suburban development, highways, and increased oil consumption.", c:"in", era:8},
  {yr:1908, yd:"1908", e:"Muller v. Oregon — Women's Work Protections", d:"Court grants women special working protections (shorter hours), recognizing their role as mothers.", c:"wo", era:8},
  {yr:1909, yd:"1909–1913", e:"Dollar Diplomacy (Taft)", d:"U.S. investment replaces military intervention in Latin America and East Asia — backfires by causing regional resentment and alienating Japan.", c:"fp", era:8},
  {yr:1910, yd:"1910–1950", e:"Modernist Literary Movement", d:"Steinbeck, Faulkner, Tennessee Williams, Arthur Miller — focused on themes of alienation and modern American life.", c:"li", era:8},
  {yr:1910, yd:"1910s", e:"NAACP Founded", d:"National Association for the Advancement of Colored People formed to fight racial segregation and discrimination through legal challenges.", c:"cr", era:8},
  {yr:1913, yd:"1913", e:"Federal Reserve Act", d:"Created 12 regional Federal Reserve banks and a Federal Reserve Board — allowed issuance of Federal Reserve Notes (U.S. Dollars), solving currency inelasticity.", c:"ec", era:8},
  {yr:1913, yd:"1913", e:"Moral Diplomacy (Wilson)", d:"The U.S. would only support democratic governments willing to negotiate peacefully — a change from commercial-based foreign policy.", c:"fp", era:8},
  {yr:1913, yd:"1913", e:"Underwood Tariff / 16th Amendment (Income Tax)", d:"Significantly cut tariff rates; the 16th Amendment enabled a graduated income tax to compensate for lost tariff revenue.", c:"ec", era:8},
  {yr:1913, yd:"1913", e:"Moving Assembly Line (Ford)", d:"Ford's Highland Park plant produces a car every 93 minutes — transforms manufacturing and enables mass consumption.", c:"in", era:8},
  {yr:1914, yd:"1914", e:"Clayton Anti-Trust Act", d:"Added to the Sherman Act — made certain business practices illegal and legalized peaceful picketing and striking for laborers.", c:"ec", era:8},
  {yr:1914, yd:"1914", e:"Federal Trade Commission", d:"Created to oversee industries in interstate commerce — could issue cease-and-desist orders against unfair practices.", c:"ec", era:8},
  {yr:1914, yd:"1914", e:"WWI Neutrality Proclamation (Wilson)", d:"Wilson proclaims U.S. neutrality in WWI, though the U.S. maintained economic ties with Britain.", c:"fp", era:8},
  {yr:1914, yd:"1914", e:"Machine Gun", d:"Rapid-fire automatic weapons first widely used in WWI — defined trench warfare.", c:"in", era:8},
  {yr:1914, yd:"1914", e:"U-boats / Submarine Warfare", d:"German submarines blockade supply ships and sink civilian vessels — sinking of the Lusitania kills 1,198.", c:"in", era:8},
  {yr:1915, yd:"1915", e:"Lusitania Sunk", d:"German U-boats sink a British passenger/munitions ship with Americans aboard, killing civilians and intensifying pressure on Wilson to enter WWI.", c:"fp", era:8},
  {yr:1915, yd:"1915", e:"Poison Gas in Warfare", d:"Germany first uses chlorine gas in Belgium — mass casualties; later banned by international treaty.", c:"in", era:8},
  {yr:1917, yd:"1917", e:"U.S. Enters WWI", d:"Following the Zimmermann Telegram and Germany resuming unrestricted submarine warfare, Wilson convinced the public the war was about democracy.", c:"fp", era:8},
  {yr:1918, yd:"1918–1935", e:"Harlem Renaissance", d:"Langston Hughes, Zora Neale Hurston, Claude McKay — Black literary and cultural movement celebrating Black identity.", c:"li", era:8},
  {yr:1919, yd:"1919", e:"Treaty of Versailles / League of Nations", d:"Wilson's 14 Points established the League of Nations at Versailles — but Congress refused to ratify because Wilson wouldn't compromise.", c:"fp", era:8},
  {yr:1919, yd:"1919", e:"Schenck v. United States", d:"Court rules free speech is not protected if it creates 'clear and present danger' — limits civil liberties during wartime.", c:"ct", era:8},
  {yr:1919, yd:"1919", e:"18th Amendment / Prohibition", d:"Prohibited the manufacture and sale of alcohol — led to speakeasies, organized crime, and eventual repeal in 1933.", c:"re", era:8},
  {yr:1920, yd:"1920", e:"19th Amendment (Women's Suffrage)", d:"Women gain the right to vote — Wilson persuaded by women's WWI contributions.", c:"wo", era:8},
  {yr:1921, yd:"1921", e:"Emergency Quota Act", d:"Limited immigration: each country may send only 3% of its people already in the U.S. (1910 census). First use of numerical immigration quotas.", c:"im", era:8},

  // Era 9 - Interwar
  {yr:1922, yd:"1922", e:"Washington Naval Conference", d:"Limits major powers' battleship inventories — U.S. and Britain maintain ships while Germany is significantly reduced.", c:"fp", era:9},
  {yr:1922, yd:"1922", e:"Fordney-McCumber Tariff", d:"High protective tariff at 40% under Harding — contributed to European inability to repay WWI debts.", c:"ec", era:9},
  {yr:1923, yd:"1923", e:"Adkins v. Children's Hospital", d:"Supreme Court strikes down minimum wage for women and children — women have equal voting rights now, so they must accept equal labor conditions (reversed Muller).", c:"ct", era:9},
  {yr:1924, yd:"1924", e:"Dawes Plan", d:"U.S. bank loans stabilize German reparations and the European economy — prevents German economic collapse.", c:"fp", era:9},
  {yr:1924, yd:"1924", e:"Immigration Act of 1924", d:"Cut quotas to 2% (based on 1890 census) — favored Northern Europeans over Southern/Eastern Europeans; entirely banned Japanese immigration.", c:"im", era:9},
  {yr:1925, yd:"1925", e:"Scopes 'Monkey' Trial", d:"Tennessee teacher John Scopes fined for teaching evolution. Conservative ruling — religion vs. science debate plays out publicly.", c:"re", era:9},
  {yr:1927, yd:"1927", e:"Television", d:"Broadcasts live video to mass public homes — eventually becomes the dominant medium of news, culture, and politics.", c:"in", era:9},
  {yr:1927, yd:"1927", e:"Sacco & Vanzetti Trial", d:"Two Italian immigrants executed for robbery/murder amid controversy — widely seen as convicted for political beliefs and immigrant status.", c:"im", era:9},
  {yr:1928, yd:"1928", e:"Kellogg-Briand Pact", d:"Makes declaring war illegal unless for defensive purposes — largely toothless but symbolically important.", c:"fp", era:9},
  {yr:1929, yd:"1929", e:"The Great Depression", d:"Stock Market Crash on Black Tuesday, caused by over-leveraged stock purchases and poor banking regulation — worst economic crisis in U.S. history.", c:"ec", era:9},
  {yr:1929, yd:"1929", e:"Agricultural Marketing Act", d:"Established the Federal Farm Board — aided farmers during early Depression through cooperatives and surplus purchases.", c:"ec", era:9},
  {yr:1930, yd:"1930", e:"Hawley-Smoot Tariff", d:"Raised tariffs to 60% — deepened the Depression by collapsing international trade.", c:"ec", era:9},
  {yr:1930, yd:"1930", e:"Nation of Islam Founded", d:"African American political and religious movement founded in Detroit by Wallace Fard Muhammad.", c:"re", era:9},
  {yr:1932, yd:"1932", e:"Norris-LaGuardia Act", d:"Outlawed anti-union contracts and barred federal courts from stopping peaceful labor protests — strengthened unions.", c:"ec", era:9},
  {yr:1933, yd:"1933", e:"New Deal (FDR)", d:"Series of relief, recovery, and reform programs including FERA, TVA, NRA, PWA, FDIC, CCC — fundamentally expands the federal government's role.", c:"ec", era:9},
  {yr:1933, yd:"1933", e:"Good Neighbor Policy", d:"FDR pledges non-intervention in Latin America at the 7th Pan American Conference.", c:"fp", era:9},
  {yr:1933, yd:"1933", e:"Frances Perkins & Mary McLeod Bethune Appointed", d:"FDR appoints Frances Perkins as the first woman in a presidential cabinet (Secretary of Labor) and Bethune as the highest-ranking African American in his administration.", c:"wo", era:9},
  {yr:1935, yd:"1935", e:"Schechter Poultry v. U.S. ('Sick Chicken Case')", d:"Supreme Court strikes down the NIRA — federal government cannot regulate local businesses under interstate commerce clause.", c:"ct", era:9},
  {yr:1935, yd:"1935–1937", e:"Three Neutrality Acts", d:"Congress bars arms sales and loans to warring nations as Hitler rises to power in Europe.", c:"fp", era:9},
  {yr:1935, yd:"1935", e:"Wagner Act / NLRB", d:"Replaced key parts of the NIRA — allows collective bargaining for labor unions.", c:"ec", era:9},
  {yr:1935, yd:"1935", e:"Social Security Act", d:"Established federal pensions for the elderly, unemployment insurance, and aid to disabled — cornerstone of the welfare state.", c:"ec", era:9},
  {yr:1938, yd:"1938", e:"Fair Labor Standards Act", d:"Set a federal minimum wage, maximum hours, and banned child labor for those under 16.", c:"ec", era:9},
  {yr:1939, yd:"1939", e:"Grapes of Wrath (John Steinbeck)", d:"Exposed the struggles of Dust Bowl migrants during the Great Depression — mobilized public sympathy for the rural poor.", c:"li", era:9},

  // Era 10 - WWII
  {yr:1941, yd:"1941", e:"Lend-Lease Act", d:"'Send guns, not sons' — provided $50 billion in war materials to Allies before official U.S. entry. Biggest recipients: UK and USSR.", c:"fp", era:10},
  {yr:1941, yd:"1941", e:"Atlantic Charter", d:"Churchill and FDR outline post-war goals and the future United Nations before the U.S. officially entered the war.", c:"fp", era:10},
  {yr:1941, yd:"1941", e:"U.S. Enters WWII (Pearl Harbor)", d:"Japan bombs Pearl Harbor on December 7, 1941. The U.S. declares war the next day.", c:"fp", era:10},
  {yr:1942, yd:"1942", e:"Executive Order 9066 / Japanese American Internment", d:"Roosevelt forces ~120,000 Japanese Americans — including U.S. citizens — into internment camps, depriving them of rights and property.", c:"im", era:10},
  {yr:1942, yd:"1942", e:"Bracero Program", d:"Agreement with Mexico to bring temporary agricultural workers to the U.S. to fill wartime labor shortages, lasting until 1964.", c:"im", era:10},
  {yr:1943, yd:"1943", e:"Tehran Conference", d:"Roosevelt, Churchill, and Stalin agree on a second front to relieve pressure on the USSR.", c:"fp", era:10},
  {yr:1944, yd:"1944", e:"D-Day (Normandy Invasion)", d:"Largest amphibious assault in history — U.S., UK, and Canada push back Nazi Germany's Atlantic Wall, turning the tide of the European war.", c:"fp", era:10},
  {yr:1944, yd:"1944", e:"Korematsu v. United States", d:"Supreme Court upholds Japanese American internment — wartime emergency justified the government's actions over 14th Amendment rights.", c:"ct", era:10},
  {yr:1945, yd:"1945", e:"Yalta Conference", d:"FDR, Churchill, and Stalin divide post-war Germany and agree to create the United Nations — seeds of Cold War tensions.", c:"fp", era:10},
  {yr:1945, yd:"1945", e:"Hiroshima and Nagasaki Bombings", d:"First military use of atomic bombs — killed 100,000+ people and forced Japan's unconditional surrender, ending WWII in the Pacific.", c:"fp", era:10},
  {yr:1945, yd:"1945", e:"Atomic Bomb (Manhattan Project)", d:"Development and first use of nuclear weapons — defines the Cold War era and begins the nuclear age.", c:"in", era:10},
  {yr:1945, yd:"1945", e:"Rosie the Riveter / Women in WWII Factories", d:"Women were encouraged to take over factory jobs while men fought. Women made up a large portion of the wartime industrial workforce.", c:"wo", era:10},
  {yr:1945, yd:"1940–1960", e:"Beat Generation", d:"Jack Kerouac, Allen Ginsberg, William Burroughs — rejected post-WWII conformity and materialism; embraced freedom and spontaneity.", c:"li", era:10},

  // Era 11 - Cold War
  {yr:1946, yd:"1946–1949", e:"Chinese Civil War", d:"U.S. sent General Marshall to negotiate between Nationalist Chiang and Communist Mao — compromise fell apart, Mao won.", c:"fp", era:11},
  {yr:1947, yd:"1947", e:"Truman Doctrine / Marshall Plan", d:"$13 billion to support anti-communist nations and rebuild war-wrecked European economies — core of the containment policy.", c:"fp", era:11},
  {yr:1947, yd:"1947", e:"National Security Act", d:"Created the CIA and reorganized U.S. military — enables systematic management of national security commitments.", c:"fp", era:11},
  {yr:1947, yd:"1947", e:"Taft-Hartley Act", d:"Anti-union legislation over Truman's veto — banned closed shops, required noncommunist oaths from union leaders, weakened New Deal labor gains.", c:"ec", era:11},
  {yr:1948, yd:"1948–1949", e:"Berlin Airlift", d:"U.S. and UK supply blockaded West Berlin with food and supplies after the USSR blocked all ground access routes.", c:"fp", era:11},
  {yr:1949, yd:"1949", e:"NATO Founded", d:"Western defense alliance to counter the USSR's growing threat — first binding U.S. military alliance since the Franco-American Alliance of 1778.", c:"fp", era:11},
  {yr:1950, yd:"1950", e:"NSC-68", d:"Key policy document calling for quadrupling U.S. military spending — classic example of military Keynesianism.", c:"fp", era:11},
  {yr:1950, yd:"1950–1953", e:"Korean War", d:"U.S. and UN forces fight North Korean invasion of South Korea to contain communism. Ceasefire along the 38th parallel in 1953.", c:"fp", era:11},
  {yr:1950, yd:"1950", e:"Sweatt v. Painter", d:"Separate Texas law school for Blacks ruled unequal — chipped away at Plessy v. Ferguson, setting the stage for Brown v. Board.", c:"ct", era:11},
  {yr:1952, yd:"1952", e:"Hydrogen Bomb", d:"More powerful than the atomic bomb — escalates Cold War nuclear arms race to existential levels.", c:"in", era:11},
  {yr:1952, yd:"1952", e:"Polio Vaccine (Jonas Salk)", d:"Vaccine practically eliminates a disease killing thousands of children — boosted public confidence in science and medicine.", c:"in", era:11},
  {yr:1953, yd:"1953", e:"Massive Retaliation Policy (Dulles)", d:"Threatened overwhelming nuclear response against communist acts — Hungarian uprising proved this policy was unrealistic.", c:"fp", era:11},
  {yr:1953, yd:"1953", e:"Suez Crisis", d:"U.S. opposes UK, France, and Israel to prevent wider Cold War conflict — marks the end of Western European dominance in the Middle East.", c:"fp", era:11},
  {yr:1954, yd:"1954", e:"Brown v. Board of Education", d:"NAACP challenge overturns Plessy v. Ferguson — separate is NOT equal; public school segregation is unconstitutional.", c:"ct", era:11},
  {yr:1954, yd:"1954", e:"Operation Wetback", d:"Program deporting up to 1 million illegal Mexican migrants — fueled by concerns about job competition with returning veterans.", c:"im", era:11},
  {yr:1955, yd:"1955", e:"Montgomery Bus Boycott", d:"Rosa Parks' arrest sparks a 381-day boycott led by Dr. Martin Luther King Jr. — pivotal early act of the Civil Rights Movement.", c:"cr", era:11},
  {yr:1956, yd:"1956", e:"U.S. Interstate Highway System", d:"Eisenhower launches 41,000-mile highway network — benefits commerce, travel, and suburban development.", c:"in", era:11},
  {yr:1957, yd:"1957", e:"Sputnik Launch / NASA", d:"USSR's first satellite shocks the U.S. — creates fear of Soviet ICBMs and launches the Space Race. NASA founded in response.", c:"fp", era:11},
  {yr:1957, yd:"1957", e:"Sputnik (Innovation)", d:"First successful artificial satellite, launched by the USSR — shocked the U.S. into the Space Race.", c:"in", era:11},
  {yr:1957, yd:"1957", e:"Little Rock Nine / Civil Rights", d:"Eisenhower sends federal troops to enforce desegregation of Central High School in Little Rock, Arkansas.", c:"cr", era:11},
  {yr:1960, yd:"1960", e:"U-2 Spy Plane Incident", d:"American spy plane shot down over the USSR — sabotages the Paris Summit and increases Cold War tensions.", c:"fp", era:11},
  {yr:1960, yd:"1960s", e:"Identity Politics / Affirmative Action", d:"Programs attempting to increase opportunities for historically discriminated groups in education and employment.", c:"cr", era:11},
  {yr:1961, yd:"1961", e:"Flexible Response Policy (JFK)", d:"Replaces massive retaliation — expands U.S. military options beyond nuclear weapons to respond proportionally to threats.", c:"fp", era:11},
  {yr:1961, yd:"1961", e:"Bay of Pigs Invasion", d:"CIA-backed attempt by Cuban exiles to overthrow Castro — fails rapidly and embarrasses the Kennedy administration.", c:"fp", era:11},
  {yr:1962, yd:"1962", e:"Cuban Missile Crisis", d:"13-day nuclear standoff after USSR places missiles in Cuba — ends with USSR removing Cuban missiles, U.S. removing missiles from Turkey.", c:"fp", era:11},
  {yr:1962, yd:"1962", e:"Engel v. Vitale", d:"State-sponsored prayer in public schools violates the First Amendment — major separation of church and state ruling.", c:"ct", era:11},
  {yr:1962, yd:"1962", e:"The Other America (Michael Harrington)", d:"Exposed dire living conditions for 40–50 million poor Americans — directly inspired LBJ's Great Society programs.", c:"li", era:11},
  {yr:1962, yd:"1962", e:"Silent Spring (Rachel Carson)", d:"Launched the modern environmental movement — directly led to the creation of the EPA.", c:"li", era:11},
  {yr:1963, yd:"1963", e:"Nuclear Test Ban Treaty", d:"Bans atmospheric nuclear testing — first step in Cold War arms control agreements.", c:"fp", era:11},
  {yr:1963, yd:"1963", e:"Gideon v. Wainwright", d:"6th Amendment requires states to provide lawyers to defendants in serious criminal cases who cannot afford one — expanded the public defender system.", c:"ct", era:11},
  {yr:1963, yd:"1963", e:"The Feminine Mystique (Betty Friedan)", d:"Challenged women to exist beyond the suburban housewife role — launched Second Wave Feminism.", c:"wo", era:11},
  {yr:1963, yd:"1963", e:"Presidential Commission on the Status of Women", d:"Established by JFK, chaired by Eleanor Roosevelt — investigated gender pay inequality and proposed reforms.", c:"wo", era:11},
  {yr:1964, yd:"1964", e:"Civil Rights Act of 1964", d:"Prohibited discrimination based on race, color, religion, sex, or national origin — landmark civil rights legislation.", c:"cr", era:11},
  {yr:1964, yd:"1964", e:"Title VII (Civil Rights Act)", d:"Prohibits employment discrimination based on sex — illegalized men-only hiring practices and protected pregnant women.", c:"wo", era:11},
  {yr:1964, yd:"1964", e:"Gulf of Tonkin Resolution", d:"Congress authorizes presidential escalation in Vietnam following a disputed attack on a U.S. ship near North Vietnam.", c:"fp", era:11},
  {yr:1964, yd:"1964–1968", e:"Great Society (LBJ)", d:"Domestic policy agenda — Medicare, Medicaid, Voting Rights Act, Civil Rights Act, Head Start, and anti-poverty programs. Successor to the New Deal.", c:"ec", era:11},
  {yr:1965, yd:"1965", e:"Voting Rights Act of 1965", d:"Prohibited discriminatory voting practices — directly addressed the 15th Amendment's failure to protect Black voting rights in the South.", c:"cr", era:11},
  {yr:1965, yd:"1965–1973", e:"Vietnam War", d:"20-year conflict to suppress the Viet Cong — included My Lai Massacre, Operation Rolling Thunder, and the Tet Offensive. Major failures reflected badly on the U.S.", c:"fp", era:11},
  {yr:1965, yd:"1965", e:"Affirmative Action (Executive Order 11246)", d:"Federal contractors required to take action against discrimination in hiring — expands opportunity for minorities and women.", c:"cr", era:11},
  {yr:1966, yd:"1966", e:"Miranda v. Arizona", d:"Law enforcement must inform suspects of their rights before interrogation — the 'Miranda warning' becomes standard procedure.", c:"ct", era:11},
  {yr:1968, yd:"1968", e:"American Indian Movement (AIM) Founded", d:"Grassroots advocacy group addressing Native poverty, police brutality, and discrimination — becomes a leading force for Indigenous civil rights.", c:"na", era:11},
  {yr:1969, yd:"1969", e:"Nixon Doctrine", d:"U.S. will aid South Vietnam financially but not fight for its allies — begins 'Vietnamization' of the war.", c:"fp", era:11},
  {yr:1969, yd:"1969", e:"Occupation of Alcatraz", d:"Indians of All Tribes occupy the former prison island for 19 months, citing the Treaty of Fort Laramie — brings global attention to Native sovereignty.", c:"na", era:11},
  {yr:1969, yd:"1969", e:"Apollo 11 / Moon Landing", d:"Saturn V rocket carries Americans to the Moon — U.S. beats the USSR in the Space Race.", c:"in", era:11},
  {yr:1972, yd:"1972", e:"SALT I (Détente)", d:"First U.S.–Soviet strategic arms limitation agreement signed by Nixon and Brezhnev — froze ICBM numbers and eased Cold War tensions.", c:"fp", era:11},
  {yr:1972, yd:"1972", e:"Title IX", d:"Prohibits sex-based discrimination in federally funded education programs — transformed women's sports and educational opportunities.", c:"wo", era:11},
  {yr:1973, yd:"1973", e:"Roe v. Wade", d:"14th Amendment protects a woman's right to privacy and liberty — legalized abortion nationwide until fetal viability.", c:"ct", era:11},
  {yr:1973, yd:"1973", e:"Paris Peace Accords", d:"U.S. withdraws from Vietnam with a ceasefire — Communist Viet Cong ultimately took control of Vietnam.", c:"fp", era:11},
  {yr:1973, yd:"1973", e:"War Powers Resolution", d:"Limits the president's power to commit troops without congressional approval — passed in response to secret bombing of Cambodia.", c:"fp", era:11},
  {yr:1974, yd:"1974", e:"United States v. Nixon", d:"Executive privilege does not extend to withholding criminal evidence — limits presidential power and forces Nixon to release the Watergate tapes.", c:"ct", era:11},
  {yr:1974, yd:"1974", e:"Milliken v. Bradley", d:"School desegregation plans cannot cross district lines — made integration nearly impossible in areas with white suburbs surrounding urban centers.", c:"ct", era:11},
  {yr:1975, yd:"1975", e:"Helsinki Accords", d:"Officially ended WWII by setting boundaries between Poland and the USSR. USSR 'guaranteed' freedoms to people in Eastern Europe.", c:"fp", era:11},
  {yr:1970, yd:"1970s", e:"Stagflation", d:"High inflation + high unemployment + low growth caused by OPEC oil embargo (1973) and Iranian Crisis (1979). Unemployment reached 9% in 1975.", c:"ec", era:11},
  {yr:1977, yd:"1977", e:"Panama Canal Treaties", d:"Carter agrees to transfer control of the Panama Canal to Panama by 1999.", c:"fp", era:11},
  {yr:1978, yd:"1978", e:"Camp David Accords", d:"Carter mediates agreement between Egypt and Israel — Egypt agrees not to invade Israel; Israel returns the Sinai Peninsula.", c:"fp", era:11},
  {yr:1978, yd:"1978", e:"Bakke v. UC Regents", d:"Strict racial quotas in university admissions ruled unconstitutional — but race may be one factor among many to achieve diversity.", c:"ct", era:11},
  {yr:1978, yd:"1978", e:"United States v. Wheeler", d:"Native American tribal land is sovereign — tribes do not need to follow state laws on reservations.", c:"ct", era:11},
  {yr:1979, yd:"1979", e:"SALT II (never ratified)", d:"Additional arms limitation treaty — Senate never ratifies due to Soviet invasion of Afghanistan.", c:"fp", era:11},
  {yr:1979, yd:"1979–1980", e:"Iranian Hostage Crisis", d:"444-day diplomatic standoff after Iran demanded extradition of the deposed Shah. Hostages released on Reagan's inauguration day.", c:"fp", era:11},

  // Era 12 - Modern
  {yr:1981, yd:"1981", e:"IBM Personal Computer", d:"First consumer-targeted personal computer — puts computing power into homes and offices.", c:"in", era:12},
  {yr:1981, yd:"1981", e:"Economic Recovery Act / Reaganomics", d:"Largest tax cut in history — cut income taxes 23% over 3 years. Supply-side economics based on trickle-down theory; also cut welfare programs while increasing defense spending.", c:"ec", era:12},
  {yr:1982, yd:"1982", e:"ERA Fails Ratification", d:"The Equal Rights Amendment, pushed by Gloria Steinem and opposed by Phyllis Schlafly, fails to be ratified by three states.", c:"wo", era:12},
  {yr:1983, yd:"1983", e:"SDI / 'Star Wars' (Reagan)", d:"Proposed space-based missile defense system — never built, but heightened Soviet fear they couldn't match U.S. in the arms race.", c:"fp", era:12},
  {yr:1983, yd:"1983", e:"Internet", d:"Uses standardized protocols to create a global network — transforms communication, commerce, warfare, and information access.", c:"in", era:12},
  {yr:1985, yd:"1985", e:"Reagan Doctrine", d:"U.S. pledges support (including military aid) to anti-communist movements fighting Soviet-backed governments.", c:"fp", era:12},
  {yr:1986, yd:"1986", e:"Tax Reform Act of 1986", d:"Created two tax brackets (15% and 28%) — reduced the top corporate tax rate from 46% to 34%. Provided significant low-income relief.", c:"ec", era:12},
  {yr:1986, yd:"1986–1987", e:"Iran-Contra Affair", d:"Reagan officials secretly sold arms to Iran and used profits to fund Nicaraguan Contras in defiance of a congressional ban.", c:"fp", era:12},
  {yr:1987, yd:"1987", e:"INF Treaty", d:"Reagan and Gorbachev eliminate intermediate-range nuclear missiles — first actual arms reduction treaty of the Cold War.", c:"fp", era:12},
  {yr:1989, yd:"1989", e:"World Wide Web", d:"System of interlinked webpages makes the internet navigable for ordinary people — launches the information age.", c:"in", era:12},
  {yr:1989, yd:"1989", e:"Webster v. Reproductive Health Services", d:"Upheld Missouri's restrictions on abortion access — allowed greater state regulation and limited Roe v. Wade.", c:"ct", era:12},
  {yr:1989, yd:"1989–1991", e:"Fall of the Berlin Wall / End of USSR", d:"Berlin Wall falls in 1989; USSR dissolved by 1991. Officially ends the Cold War, leaving the U.S. as the sole global superpower.", c:"fp", era:12},
  {yr:1990, yd:"1990", e:"Native American Graves Protection and Repatriation Act", d:"Federal law requires museums and agencies to return Indigenous remains, funerary objects, and sacred items to affiliated tribes.", c:"na", era:12},
  {yr:1990, yd:"1990–1991", e:"Persian Gulf War / Operation Desert Storm", d:"U.S.-led coalition of 34 nations drives Iraq out of Kuwait in six weeks after Saddam Hussein's invasion.", c:"fp", era:12},
  {yr:1990, yd:"1990s", e:"Globalization", d:"Fall of the Soviet Union and rapid tech growth fueled corporate global expansion — increased competition for blue-collar workers; created the WTO and NAFTA.", c:"ec", era:12},
  {yr:1992, yd:"1992", e:"Planned Parenthood v. Casey", d:"Reaffirmed Roe's constitutional right to abortion but allowed state restrictions that don't create an 'undue burden.'", c:"ct", era:12},
  {yr:1993, yd:"1993", e:"Family and Medical Leave Act", d:"Requires employers to provide unpaid leave for family medical needs — significant advancement for working women.", c:"wo", era:12},
  {yr:1994, yd:"1994", e:"NAFTA", d:"Free trade agreement between U.S., Canada, and Mexico — eliminated most tariffs, boosted trade, but controversial for perceived job losses.", c:"fp", era:12},
  {yr:1994, yd:"1994", e:"Violence Against Women Act", d:"Federal enforcement against domestic violence, sexual assault, and stalking.", c:"wo", era:12},
  {yr:1995, yd:"1995–2002", e:"Dot-Com Bubble", d:"Rapid surge in tech stocks fueled by internet optimism — massive overinvestment ended in a $5 trillion crash from 2001–2002.", c:"ec", era:12},
  {yr:1995, yd:"1995, 1999", e:"Bosnia and Kosovo Interventions", d:"U.S.-led NATO air campaigns stop ethnic cleansing in former Yugoslavia — first major use of military force for humanitarian purposes.", c:"fp", era:12},
  {yr:1996, yd:"1996", e:"IIRIRA (Illegal Immigration Reform Act)", d:"Strengthened border enforcement, increased penalties for illegal immigration, restricted relief and public benefits for undocumented immigrants.", c:"im", era:12},
  {yr:2000, yd:"2000", e:"Bush v. Gore", d:"Supreme Court stops Florida's manual recount — decides the 2000 presidential election in George W. Bush's favor.", c:"ct", era:12},
  {yr:2001, yd:"2001–2014", e:"Afghanistan War", d:"U.S. and NATO invade Afghanistan to destroy al-Qaeda and remove the Taliban for sheltering them. America's longest war.", c:"fp", era:12},
  {yr:2002, yd:"2002–2011", e:"Iraq War / Bush Doctrine", d:"Bush asserts the right to preemptive war and invades Iraq claiming WMDs — none were found. Eventually destabilizes the region.", c:"fp", era:12},
  {yr:2007, yd:"2007–2009", e:"Great Recession / 2008 Financial Crisis", d:"Burst of the housing market (toxic loans, CDOs) leads to the worst recession since the Great Depression.", c:"ec", era:12},
  {yr:2009, yd:"2009", e:"American Recovery and Reinvestment Act", d:"Obama's $831 billion stimulus package — tax cuts, unemployment benefits, and federal funding to combat the Great Recession.", c:"ec", era:12},
  {yr:2010, yd:"2010", e:"Citizens United v. FEC", d:"First Amendment protects corporations — spending money to influence elections is protected free speech.", c:"ct", era:12},
  {yr:2010, yd:"2010", e:"Dodd-Frank Act", d:"Financial regulation reform — implemented the Volcker Rule, created the Consumer Financial Protection Bureau, established oversight of systemically important banks.", c:"ec", era:12},
  {yr:2010, yd:"2010", e:"Indian Healthcare Improvement Act", d:"Permanently authorizes federal health services for Native Americans as part of the Affordable Care Act.", c:"na", era:12},
  {yr:2011, yd:"2011", e:"Osama bin Laden Killed", d:"U.S. Navy SEALs kill bin Laden in Pakistan — without informing the Pakistani government.", c:"fp", era:12},
  {yr:2012, yd:"2012", e:"DACA (Deferred Action for Childhood Arrivals)", d:"Granted undocumented immigrants who arrived under age 16 protection from deportation and work permits. Ended in 2017 under Trump.", c:"im", era:12},
  {yr:2022, yd:"2022", e:"Dobbs v. Jackson Women's Health Organization", d:"Overturns Roe v. Wade — eliminates the constitutional right to abortion, returning the issue to individual states.", c:"ct", era:12}
];

const catLabels = {
  fp:"Foreign Policy", ec:"Economics", na:"Native Americans",
  wo:"Women", ct:"Court Cases", li:"Literature/Culture",
  in:"Innovations", re:"Religion/Education", im:"Immigration", cr:"Civil Rights"
};

let activeCats = new Set(Object.keys(catLabels));
let activeEra = "all";
let searchTerm = "";

function render() {
  const wrap = document.getElementById("timelineWrap");
  wrap.innerHTML = "";
  let totalVisible = 0;

  const search = searchTerm.toLowerCase();

  ERAS.forEach(era => {
    if (activeEra !== "all" && parseInt(activeEra) !== era.num) return;

    const events = EVENTS.filter(ev => {
      if (ev.era !== era.num) return false;
      if (!activeCats.has(ev.c)) return false;
      if (search && !ev.e.toLowerCase().includes(search) && !ev.d.toLowerCase().includes(search)) return false;
      return true;
    }).sort((a,b) => a.yr - b.yr);

    if (events.length === 0) return;
    totalVisible += events.length;

    const block = document.createElement("div");
    block.className = "era-block";

    block.innerHTML = `
      <div class="era-header">
        <div class="era-num">${era.num}</div>
        <div>
          <div class="era-title">${era.title}</div>
          <div class="era-years">${era.years}</div>
        </div>
      </div>
      <div class="events-list" id="era-${era.num}-list"></div>
    `;

    wrap.appendChild(block);
    const list = block.querySelector(`#era-${era.num}-list`);

    events.forEach(ev => {
      const item = document.createElement("div");
      item.className = "event-item";
      item.innerHTML = `
        <div class="event-top">
          <span class="event-year">${ev.yd}</span>
          <span class="event-title">${ev.e}</span>
          <span class="event-tag ${ev.c}">${catLabels[ev.c]}</span>
        </div>
        <div class="event-desc">${ev.d}</div>
      `;
      item.addEventListener("click", () => item.classList.toggle("open"));
      list.appendChild(item);
    });
  });

  if (totalVisible === 0) {
    wrap.innerHTML = '<div class="no-results">No events match your current filters.</div>';
  }

  document.getElementById("counter").textContent = `${totalVisible} event${totalVisible !== 1 ? "s" : ""}`;
}

document.querySelectorAll(".cat-btn").forEach(btn => {
  btn.addEventListener("click", () => {
    const cat = btn.dataset.cat;
    if (activeCats.has(cat)) {
      activeCats.delete(cat);
      btn.classList.remove("active");
      btn.classList.add("inactive");
    } else {
      activeCats.add(cat);
      btn.classList.add("active");
      btn.classList.remove("inactive");
    }
    render();
  });
});

document.getElementById("eraFilter").addEventListener("change", e => {
  activeEra = e.target.value;
  render();
});

document.getElementById("search").addEventListener("input", e => {
  searchTerm = e.target.value;
  render();
});

render();
</script>
