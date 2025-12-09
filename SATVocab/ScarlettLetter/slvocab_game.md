---
title: Military Test
layout: post
permalink: /mltest
author: Anwita Bandaru
---

<div id="sl-quiz" style="max-width:1000px;margin:auto;">

<html>
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<link href="https://fonts.googleapis.com/css2?family=Lora:wght@400;600&display=swap" rel="stylesheet">

<style>
body, #sl-quiz {
  font-family: 'Lora', serif;
  background: #2b284bff;
  color: #f4efe2;
  line-height: 1.6;
}

/* Layout */
#layout {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
@media (min-width: 850px) {
  #layout { flex-direction: row; align-items: flex-start; }
}

/* Quiz Wrapper */
#quizWrapper {
  background: #6c5c40ff;
  padding: 1.5rem;
  border-radius: .5rem;
  border: 1px solid #d2c7b3;
  flex: 2;
  color: #fffaf0;
}

/* Sidebar */
#sidebar {
  flex: 1;
  background: #978567ff;
  border: 1px solid #d2c7b3;
  border-radius: .5rem;
  padding: 1rem;
  max-height: 85vh;
  overflow-y: auto;
  color: #fff8ec;
}
#sidebar h3 {
  color: #2d2a26;
  margin-top: 0;
  font-weight: 600;
}

/* Chapter Selector */
.chapter-row { display: flex; flex-wrap: wrap; gap: .5rem; }
.chapter-row label {
  background: #b8a787;
  padding: .25rem .5rem;
  border-radius: .3rem;
  cursor: pointer;
  color: #2d2a26;
}
.chapter-row input { margin-right: .25rem; }

/* Options */
.option {
  background: #b8a787ff;
  color: #2d2a26;
  padding: .6rem;
  border-radius: .3rem;
  margin: .25rem 0;
  cursor: pointer;
}
.option:hover { background: #e8dbc3; }
.option.selected {
  border: 1px solid #b18c5a;
  background: #f0e6d3;
}

/* Buttons */
.btn {
  background: #d2c7b3;
  color: #2d2a26;
  border: none;
  border-radius: .3rem;
  padding: .5rem 1rem;
  margin-top: 1rem;
  cursor: pointer;
  font-family: inherit;
}
.btn:hover { background: #c6b79c; }

/* Progress Bar */
.progress {
  height: 8px;
  background: #e5dcc8;
  border-radius: 6px;
  overflow: hidden;
  margin-top: 8px;
}
.bar {
  height: 100%;
  background: #4b4871ff;
  width: 0%;
  transition: width .3s ease;
}

.meta { color: #f4efe2; margin-top: 8px; font-size: 14px; }
#explainBox {
  margin-top: 1rem;
  display: none;
  color: #f3e9d8;
  font-style: italic;
}
</style>
</head>

<body>

<div id="layout">

  <!-- Quiz Section -->
  <div id="quizWrapper">
    <h2 style="color:#2d2a26;">Scarlet Letter Vocabulary Quiz</h2>

    <div class="chapter-box">
      <h3>Select Chapters</h3>
      <div class="chapter-row" id="chapterSelect"></div>
      <div style="margin-top: 1rem;">
        <label style="display: flex; align-items: center; gap: 0.5rem; cursor: pointer; color: #2d2a26; font-weight: 600;">
          <input type="checkbox" id="requiredOnly" style="width: auto;">
          Required Words Only
        </label>
      </div>
      <button class="btn" id="startBtn">Start Quiz</button>
    </div>

    <div id="definitionBox" style="font-size:18px;font-weight:600;margin-bottom:12px;">
      Select chapters to begin.
    </div>

    <div id="options"></div>
    <button id="submitBtn" class="btn" style="display:none;">Submit</button>
    <button id="nextBtn" class="btn" style="display:none;">Next</button>

    <div id="explainBox"></div>

    <div class="progress"><div class="bar" id="progressBar"></div></div>
    <p id="scoreText" class="meta">0 correct</p>
    
  </div>

  <!-- Sidebar -->
  <div id="sidebar">
    <h3>Previous Word</h3>
    <div id="previousWord"><small>None yet</small></div>
    <hr>
    <h3>Seen Words</h3>
    <div id="seenList"></div>
  </div>

</div>

<script>
/* -----------------------------
   Load Scarlet Letter JSON Data
----------------------------- */
const data = {
  "chapters": {
    "1": [
      {
        "word": "beetle-browed",
        "definition": "frowning; scowling [describes the upper floor of the jail, which jutted out over the lower floor]",
        "required": true
      },
      {
        "word": "ponderous",
        "definition": "very heavy; massive",
        "required": true
      },
      {
        "word": "pertains",
        "definition": "concerns; has to do with",
        "required": true
      },
      {
        "word": "edifice",
        "definition": "a building, esp. a large imposing one",
        "required": true
      },
      {
        "word": "Ann (or Anne) Hutchinson",
        "definition": "American religious leader (1591-1643)",
        "required": false
      },
      {
        "word": "inauspicious",
        "definition": "not favorable; unlucky",
        "required": true
      }
    ],
    "2": [
      {
        "word": "physiognomies",
        "definition": "facial features (especially as clues to character)",
        "required": true
      },
      {
        "word": "indubitably",
        "definition": "unquestionably",
        "required": true
      },
      {
        "word": "Antinomian",
        "definition": "a member of a Christian sect whose believers hold that faith alone, not obedience to the moral law, is necessary for salvation",
        "required": false
      },
      {
        "word": "heterodox",
        "definition": "departing from the usual beliefs; unorthodox",
        "required": true
      },
      {
        "word": "venerable",
        "definition": "impressive because of age or historic or religious associations",
        "required": true
      },
      {
        "word": "farthingale",
        "definition": "a hoop skirt",
        "required": false
      },
      {
        "word": "purport",
        "definition": "meaning; intention",
        "required": false
      },
      {
        "word": "behoof",
        "definition": "interest; benefit",
        "required": false
      },
      {
        "word": "gossips",
        "definition": "good friends (arch.); people who repeat rumors about the private affairs of others",
        "required": false
      },
      {
        "word": "trow",
        "definition": "to believe; to think",
        "required": false
      },
      {
        "word": "brave",
        "definition": "bold; courageous; defiant",
        "required": false
      },
      {
        "word": "town beadle",
        "definition": "a minor official of the court",
        "required": false
      },
      {
        "word": "sumptuary",
        "definition": "intended to regulate extravagance on religious or moral grounds",
        "required": true
      },
      {
        "word": "iniquity",
        "definition": "wickedness; an unjust or unrighteous act",
        "required": true
      },
      {
        "word": "ignominious",
        "definition": "shameful; humiliating",
        "required": true
      },
      {
        "word": "haughty",
        "definition": "proud in a scornful way; arrogant",
        "required": true
      },
      {
        "word": "perchance",
        "definition": "possibly",
        "required": false
      },
      {
        "word": "rankles",
        "definition": "causes anger or resentment",
        "required": true
      },
      {
        "word": "serene",
        "definition": "calm; peaceful",
        "required": true
      },
      {
        "word": "pillory",
        "definition": "a device in which a prisoner is locked and exposed to public humiliation",
        "required": true
      },
      {
        "word": "gripe",
        "definition": "a hold; a grip",
        "required": false
      },
      {
        "word": "Papist",
        "definition": "a Roman Catholic (often a derogatory term)",
        "required": false
      },
      {
        "word": "personages",
        "definition": "people of importance or distinction",
        "required": false
      },
      {
        "word": "inferred",
        "definition": "drawn as a conclusion",
        "required": true
      },
      {
        "word": "contumely",
        "definition": "insulting rudeness; scorn",
        "required": true
      },
      {
        "word": "disdainful",
        "definition": "proudly aloof; scornful",
        "required": true
      },
      {
        "word": "preternaturally",
        "definition": "beyond what is normally found in nature; supernaturally",
        "required": false
      },
      {
        "word": "phantasmagoric",
        "definition": "of a rapidly changing series of images",
        "required": true
      },
      {
        "word": "remonstrance",
        "definition": "an objection; a complaint",
        "required": false
      },
      {
        "word": "cloister",
        "definition": "a monastery or convent",
        "required": false
      }
    ],
    "3": [
      {
        "word": "visage",
        "definition": "face; facial features",
        "required": true
      },
      {
        "word": "manifest",
        "definition": "evident; obvious",
        "required": true
      },
      {
        "word": "heterogeneous",
        "definition": "of different origins; not of the same kind",
        "required": true
      },
      {
        "word": "intervolutions",
        "definition": "twistings together",
        "required": false
      },
      {
        "word": "imperceptible",
        "definition": "not easily noticeable",
        "required": true
      },
      {
        "word": "wherefore",
        "definition": "why; for what reason",
        "required": false
      },
      {
        "word": "methinks",
        "definition": "it seems to me",
        "required": false
      },
      {
        "word": "agone",
        "definition": "ago",
        "required": false
      },
      {
        "word": "marry",
        "definition": "exclamation for emphasis",
        "required": false
      },
      {
        "word": "misguidance",
        "definition": "poor judgment leading to misconduct",
        "required": false
      },
      {
        "word": "conceive",
        "definition": "to understand",
        "required": false
      },
      {
        "word": "peradventure",
        "definition": "possibly; perhaps",
        "required": false
      },
      {
        "word": "behooves",
        "definition": "is necessary for, is appropriate for",
        "required": false
      },
      {
        "word": "sagacity",
        "definition": "wisdom; sound judgment",
        "required": true
      },
      {
        "word": "eminent",
        "definition": "distinguished; high in rank or position",
        "required": true
      },
      {
        "word": "mien",
        "definition": "a person's manner or way of carrying himself or herself",
        "required": true
      },
      {
        "word": "withal",
        "definition": "besides; in addition",
        "required": false
      },
      {
        "word": "tremulous",
        "definition": "quivering; trembling",
        "required": false
      },
      {
        "word": "effectual",
        "definition": "likely to produce",
        "required": false
      },
      {
        "word": "insensibility",
        "definition": "unawareness; indifference",
        "required": false
      }
    ],
    "4": [
      {
        "word": "pervaded",
        "definition": "spread throughout",
        "required": true
      },
      {
        "word": "interpret",
        "definition": "to reveal or explain",
        "required": false
      },
      {
        "word": "type",
        "definition": "a perfect example",
        "required": false
      },
      {
        "word": "sagamores",
        "definition": "chiefs; tribal leaders",
        "required": false
      },
      {
        "word": "prithee",
        "definition": "please",
        "required": false
      },
      {
        "word": "amenable",
        "definition": "responsive; cooperative",
        "required": true
      },
      {
        "word": "demeanor",
        "definition": "outward behavior",
        "required": false
      },
      {
        "word": "intimated",
        "definition": "hinted at",
        "required": false
      },
      {
        "word": "peremptory",
        "definition": "absolute; undeniable; final",
        "required": true
      },
      {
        "word": "simples",
        "definition": "medicinal herbs",
        "required": false
      },
      {
        "word": "repelled",
        "definition": "refused to accept",
        "required": false
      },
      {
        "word": "misbegotten",
        "definition": "of wrongful origin",
        "required": false
      },
      {
        "word": "efficacy",
        "definition": "effectiveness",
        "required": false
      },
      {
        "word": "leech",
        "definition": "physician",
        "required": false
      },
      {
        "word": "Lethe nor Nepenthe",
        "definition": "According to an ancient Greek myth, drinking water of Lethe, a river in Hades, induced forgetfulness. Nepenthe was a drug supposed by the ancient Greeks to cause forgetfulness of sorrow.",
        "required": false
      },
      {
        "word": "requital",
        "definition": "something given in return",
        "required": true
      },
      {
        "word": "Paracelsus",
        "definition": "Swiss physician and alchemist (1493-1541)",
        "required": false
      },
      {
        "word": "expostulation",
        "definition": "strong objection",
        "required": true
      },
      {
        "word": "bale-fire",
        "definition": "bonfire; beacon fire",
        "required": false
      },
      {
        "word": "feigned",
        "definition": "pretended",
        "required": false
      },
      {
        "word": "ligaments",
        "definition": "ties; bonds",
        "required": false
      },
      {
        "word": "wottest",
        "definition": "know",
        "required": false
      }
    ],
    "5": [
      {
        "word": "lurid",
        "definition": "vivid in a shocking way; sensational",
        "required": true
      },
      {
        "word": "annihilate",
        "definition": "to destroy completely",
        "required": false
      },
      {
        "word": "vivify",
        "definition": "to give life to; animate",
        "required": true
      },
      {
        "word": "inscrutable",
        "definition": "mysterious; not easily understood",
        "required": true
      },
      {
        "word": "fain",
        "definition": "gladly",
        "required": false
      },
      {
        "word": "inquisitorial",
        "definition": "harshly prying or questioning",
        "required": true
      },
      {
        "word": "repugnance",
        "definition": "extreme distaste",
        "required": true
      },
      {
        "word": "exhortation",
        "definition": "an earnest warning; a strong urging",
        "required": true
      },
      {
        "word": "contumaciously",
        "definition": "disobediently",
        "required": true
      },
      {
        "word": "talisman",
        "definition": "an object with magic power; a charm",
        "required": true
      }
    ],
    "6": [
      {
        "word": "apprehension",
        "definition": "anxious feeling about the future",
        "required": true
      },
      {
        "word": "mutability",
        "definition": "changeability",
        "required": true
      },
      {
        "word": "prolific of",
        "definition": "likely to bring forth",
        "required": false
      },
      {
        "word": "caprice",
        "definition": "whim; sudden change of mind",
        "required": true
      },
      {
        "word": "inexplicable",
        "definition": "that which cannot be explained or understood",
        "required": false
      },
      {
        "word": "perverse",
        "definition": "different from what is considered right; contrary",
        "required": true
      },
      {
        "word": "malicious",
        "definition": "spiteful; intentionally harmful",
        "required": true
      },
      {
        "word": "intangibility",
        "definition": "without physical substance",
        "required": false
      },
      {
        "word": "constrained",
        "definition": "forced",
        "required": false
      },
      {
        "word": "evoked",
        "definition": "called forth",
        "required": true
      },
      {
        "word": "inviolable",
        "definition": "sacred; not to be injured",
        "required": true
      },
      {
        "word": "anathemas",
        "definition": "strong curses; condemnations",
        "required": false
      },
      {
        "word": "reviled",
        "definition": "used abusive language toward",
        "required": false
      },
      {
        "word": "gesticulation",
        "definition": "energetic gesturing",
        "required": false
      },
      {
        "word": "freak",
        "definition": "an odd or unexpected idea; a whim",
        "required": false
      },
      {
        "word": "labyrinth",
        "definition": "maze",
        "required": true
      }
    ],
    "7": [
      {
        "word": "impelled",
        "definition": "drove; forced; compelled",
        "required": true
      },
      {
        "word": "cabalistic",
        "definition": "secret; mysterious; having to do with a mystical interpretation of scriptures developed in the Middle Ages",
        "required": false
      },
      {
        "word": "imperatively",
        "definition": "in a demanding way",
        "required": true
      },
      {
        "word": "bond-servants",
        "definition": "persons who serve a master without pay, usually in return for passage or other consideration",
        "required": false
      },
      {
        "word": "ruffs",
        "definition": "high, stiff collars worn by both men and women in the sixteenth and seventeenth centuries",
        "required": false
      },
      {
        "word": "panoply",
        "definition": "a complete suit of armor",
        "required": false
      },
      {
        "word": "Pequod (Pequot) war",
        "definition": "a war that took place between the Pequots, an Algonquian people who controlled eastern Connecticut, and the British",
        "required": false
      },
      {
        "word": "Bacon, Coke, Noye, and Finch",
        "definition": "famous British legal experts",
        "required": false
      },
      {
        "word": "eldritch",
        "definition": "weird; eerie",
        "required": false
      }
    ],
    "8": [
      {
        "word": "endue",
        "definition": "to put on; to dress in",
        "required": false
      },
      {
        "word": "expatiating",
        "definition": "explaining in great detail",
        "required": false
      },
      {
        "word": "charger",
        "definition": "a plate or platter [In the Bible, Salome demands and gets the head of John the Baptist on a charger- Mark 6:21-28.]",
        "required": false
      },
      {
        "word": "behest",
        "definition": "bidding; command",
        "required": false
      },
      {
        "word": "reproof",
        "definition": "disapproval; censure",
        "required": false
      },
      {
        "word": "transgressions",
        "definition": "sins; acts that are against the law",
        "required": true
      },
      {
        "word": "Lord of Misrule",
        "definition": "master of revels in medieval Christmas celebrations, often assisted by young pranksters",
        "required": false
      },
      {
        "word": "bedizen",
        "definition": "to dress or decorate in a showy way",
        "required": false
      },
      {
        "word": "albeit",
        "definition": "even though",
        "required": false
      },
      {
        "word": "warily",
        "definition": "cautiously",
        "required": false
      },
      {
        "word": "nurture",
        "definition": "training; upbringing",
        "required": false
      },
      {
        "word": "imbibes",
        "definition": "drinks in; absorbs",
        "required": false
      },
      {
        "word": "indefeasible",
        "definition": "that cannot be taken away",
        "required": false
      },
      {
        "word": "mountebank",
        "definition": "one who entertains with jokes or tricks",
        "required": false
      },
      {
        "word": "adduced",
        "definition": "stated as reasons",
        "required": false
      },
      {
        "word": "tithing-men",
        "definition": "church officials who collected money to support the church and generally saw to the observance of community rules",
        "required": false
      },
      {
        "word": "unobtrusive",
        "definition": "inconspicuous; modest",
        "required": true
      },
      {
        "word": "averred",
        "definition": "declared to be true",
        "required": true
      }
    ],
    "9": [
      {
        "word": "appellation",
        "definition": "a name",
        "required": false
      },
      {
        "word": "vindicate",
        "definition": "to lay claim to; to establish possession of",
        "required": true
      },
      {
        "word": "consigned",
        "definition": "sent, esp., to an undesirable place or position",
        "required": false
      },
      {
        "word": "chirurgical",
        "definition": "surgical",
        "required": false
      },
      {
        "word": "physic",
        "definition": "medical science",
        "required": false
      },
      {
        "word": "Elixir of Life",
        "definition": "substance supposedly able to cure all diseases",
        "required": false
      },
      {
        "word": "pharmacopoeia",
        "definition": "stock of medicines",
        "required": false
      },
      {
        "word": "exemplary",
        "definition": "(1) serving as a model; worth imitating; (2) serving as a warning (exemplary punishment)",
        "required": true
      },
      {
        "word": "parochial",
        "definition": "having to do with affairs of the parish; local",
        "required": false
      },
      {
        "word": "emaciated",
        "definition": "abnormally lean, as from starvation or illness",
        "required": true
      },
      {
        "word": "imminent",
        "definition": "likely to happen very soon",
        "required": true
      },
      {
        "word": "providential",
        "definition": "showing the guidance of God",
        "required": true
      },
      {
        "word": "despondent",
        "definition": "lacking in hope; pessimistic",
        "required": true
      },
      {
        "word": "importunate",
        "definition": "annoyingly persistent; insistent",
        "required": true
      },
      {
        "word": "celibacy",
        "definition": "the state of being unmarried, esp. that of a person under a vow not to marry",
        "required": false
      },
      {
        "word": "emissary",
        "definition": "a person sent on a special mission; an agent",
        "required": true
      }
    ],
    "10": [
      {
        "word": "Bunyan's awful doorway",
        "definition": "the gates of Hell in John Bunyan's The Pilgrim's Progress",
        "required": false
      },
      {
        "word": "premeditated",
        "definition": "planned beforehand",
        "required": true
      },
      {
        "word": "inimical",
        "definition": "hostile; in opposition",
        "required": true
      },
      {
        "word": "potency",
        "definition": "effectiveness; strength",
        "required": true
      },
      {
        "word": "forebode",
        "definition": "to predict; to foretell",
        "required": true
      },
      {
        "word": "perforce",
        "definition": "necessarily",
        "required": false
      },
      {
        "word": "propagate",
        "definition": "to breed",
        "required": false
      },
      {
        "word": "penitential",
        "definition": "expressing sorrow at having sinned",
        "required": true
      },
      {
        "word": "Providence",
        "definition": "the guidance or direction of God",
        "required": true
      },
      {
        "word": "child's play",
        "definition": "usually, an easy task; here, foolish or childish behavior",
        "required": false
      },
      {
        "word": "imbued",
        "definition": "saturated; filled",
        "required": false
      },
      {
        "word": "palliate",
        "definition": "to make seem less serious or offensive",
        "required": true
      },
      {
        "word": "somniferous",
        "definition": "sleep-inducing",
        "required": true
      }
    ],
    "11": [
      {
        "word": "forlorn",
        "definition": "abandoned; miserable",
        "required": true
      },
      {
        "word": "machinations",
        "definition": "schemes of evil intent",
        "required": false
      },
      {
        "word": "abstruse",
        "definition": "hard to understand",
        "required": false
      },
      {
        "word": "unamiable",
        "definition": "usually, unfriendly; here, cold or stiff",
        "required": true
      },
      {
        "word": "veneration",
        "definition": "profound respect",
        "required": true
      },
      {
        "word": "abomination",
        "definition": "something hateful and disgusting",
        "required": true
      },
      {
        "word": "hypocrite",
        "definition": "one who pretends to be what he/she is not",
        "required": true
      },
      {
        "word": "put a cheat upon",
        "definition": "deceive",
        "required": false
      },
      {
        "word": "introspection",
        "definition": "examination of one's own thoughts and feelings",
        "required": true
      },
      {
        "word": "ethereal",
        "definition": "not earthly; heavenly",
        "required": true
      },
      {
        "word": "deluded",
        "definition": "deceived; fooled",
        "required": true
      },
      {
        "word": "impalpable",
        "definition": "not perceptible to the touch; too subtle to be grasped by the mind",
        "required": true
      }
    ],
    "12": [
      {
        "word": "somnambulism",
        "definition": "sleepwalking",
        "required": false
      },
      {
        "word": "obscure",
        "definition": "dark and murky",
        "required": true
      },
      {
        "word": "catarrh",
        "definition": "inflammation of the nose or throat",
        "required": false
      },
      {
        "word": "expiation",
        "definition": "atonement",
        "required": true
      },
      {
        "word": "luminary",
        "definition": "something that gives off light; a person who enlightens mankind",
        "required": true
      },
      {
        "word": "defunct",
        "definition": "no longer alive",
        "required": true
      },
      {
        "word": "torpid",
        "definition": "without sensation; sluggish",
        "required": false
      },
      {
        "word": "scurrilous",
        "definition": "coarse; vulgar",
        "required": false
      }
    ],
    "13": [
      {
        "word": "pristine",
        "definition": "pure; unspoiled; of an earlier condition",
        "required": true
      },
      {
        "word": "morbid",
        "definition": "usually, gruesome; here, unwholesome, resulting from a diseased state of mind; resulting from disease",
        "required": true
      },
      {
        "word": "pestilence",
        "definition": "infectious disease",
        "required": true
      },
      {
        "word": "calamity",
        "definition": "a disaster; an extreme misfortune",
        "required": true
      },
      {
        "word": "despotic",
        "definition": "like an absolute ruler or tyrant",
        "required": true
      },
      {
        "word": "auspicious",
        "definition": "favorable; promising well for the future",
        "required": true
      }
    ],
    "14": [
      {
        "word": "accosted",
        "definition": "approached and spoke to",
        "required": false
      },
      {
        "word": "extort",
        "definition": "to get by force or threats",
        "required": true
      },
      {
        "word": "propinquity",
        "definition": "nearness",
        "required": false
      },
      {
        "word": "casual",
        "definition": "not planned; incidental",
        "required": false
      }
    ],
    "15": [
      {
        "word": "sedulous",
        "definition": "hardworking; diligent",
        "required": false
      },
      {
        "word": "deleterious",
        "definition": "harmful to health or well-being",
        "required": false
      },
      {
        "word": "malignant",
        "definition": "very dangerous",
        "required": true
      },
      {
        "word": "nightshade, dogwood, and henbane",
        "definition": "types of plants (nightshade and henbane are poisonous; all three were supposedly used in witches' potions)",
        "required": false
      },
      {
        "word": "nuptial",
        "definition": "marital",
        "required": false
      },
      {
        "word": "wrought upon",
        "definition": "prevailed upon",
        "required": false
      },
      {
        "word": "wrought out",
        "definition": "produced",
        "required": false
      },
      {
        "word": "horseshoe",
        "definition": "a horseshoe crab",
        "required": false
      },
      {
        "word": "five-fingers",
        "definition": "a starfish",
        "required": false
      },
      {
        "word": "hornbook",
        "definition": "a tablet used for teaching spelling",
        "required": false
      },
      {
        "word": "capricious",
        "definition": "changeable; flighty",
        "required": true
      },
      {
        "word": "unwonted",
        "definition": "unusual; unaccustomed",
        "required": false
      },
      {
        "word": "enigma",
        "definition": "something or someone that is puzzling or seems impossible to explain",
        "required": true
      },
      {
        "word": "propensity",
        "definition": "inclination; tendency",
        "required": true
      },
      {
        "word": "beneficence",
        "definition": "doing good; kindness",
        "required": false
      },
      {
        "word": "asperity",
        "definition": "sharpness; harshness of temper",
        "required": true
      }
    ],
    "16": [
      {
        "word": "Apostle Eliot",
        "definition": "John Eliot (1604-1690) came to Boston in 1630 and preached to the American Indians in their own languages.",
        "required": false
      },
      {
        "word": "scrofula",
        "definition": "usually, a noncontagious form of tuberculosis; here, symbolizing troubles children inherit from parents and ancestors",
        "required": false
      },
      {
        "word": "wanted",
        "definition": "lacked; had need of",
        "required": false
      },
      {
        "word": "loquacity",
        "definition": "excessive talkativeness",
        "required": false
      },
      {
        "word": "lamentation",
        "definition": "an outward expression of grief",
        "required": true
      },
      {
        "word": "repining",
        "definition": "unhappy; complaining",
        "required": false
      },
      {
        "word": "vivacious",
        "definition": "hard to kill; long-lived",
        "required": false
      }
    ],
    "17": [
      {
        "word": "wonted",
        "definition": "accustomed",
        "required": false
      },
      {
        "word": "contiguity",
        "definition": "nearness",
        "required": false
      },
      {
        "word": "misanthropy",
        "definition": "dislike or distrust of people",
        "required": true
      },
      {
        "word": "transfiguration",
        "definition": "a radical change in form or appearance",
        "required": true
      },
      {
        "word": "consecration",
        "definition": "holiness; sacredness",
        "required": false
      },
      {
        "word": "cumber",
        "definition": "to interfere with; to hamper",
        "required": false
      }
    ],
    "18": [
      {
        "word": "colloquy",
        "definition": "a serious conversation; a formal discussion",
        "required": true
      },
      {
        "word": "earnest",
        "definition": "a pledge; a token",
        "required": false
      },
      {
        "word": "solace",
        "definition": "consolation; comfort",
        "required": true
      },
      {
        "word": "stigma",
        "definition": "a mark or sign of disgrace",
        "required": true
      },
      {
        "word": "effluence",
        "definition": "a flowing forth",
        "required": false
      },
      {
        "word": "familiar",
        "definition": "easy and informal",
        "required": false
      },
      {
        "word": "choleric",
        "definition": "quick-tempered",
        "required": true
      }
    ],
    "19": [
      {
        "word": "inured",
        "definition": "accustomed to something painful or difficult",
        "required": true
      },
      {
        "word": "mollified",
        "definition": "soothed; pacified",
        "required": true
      },
      {
        "word": "inevitable",
        "definition": "certain to happen",
        "required": true
      }
    ],
    "20": [
      {
        "word": "vicissitude",
        "definition": "unforeseeable change",
        "required": true
      },
      {
        "word": "Spanish Main",
        "definition": "the Caribbean and its coastal areas",
        "required": false
      },
      {
        "word": "irrefragable",
        "definition": "indisputable",
        "required": true
      },
      {
        "word": "comport",
        "definition": "to behave",
        "required": false
      },
      {
        "word": "obeisance",
        "definition": "a respectful attitude; deference",
        "required": true
      },
      {
        "word": "instilment",
        "definition": "putting in drop by drop",
        "required": false
      },
      {
        "word": "buckramed",
        "definition": "very stiff and formal",
        "required": false
      }
    ],
    "21": [
      {
        "word": "betimes",
        "definition": "early; promptly",
        "required": false
      },
      {
        "word": "plebeian",
        "definition": "of the ordinary people",
        "required": true
      },
      {
        "word": "wormwood and aloes",
        "definition": "bitter herbs",
        "required": false
      },
      {
        "word": "effervescence",
        "definition": "high-spiritedness",
        "required": false
      },
      {
        "word": "affliction",
        "definition": "something causing pain and distress; a misfortune",
        "required": true
      },
      {
        "word": "countenanced",
        "definition": "indulged; permitted",
        "required": false
      },
      {
        "word": "gleeman",
        "definition": "a medieval minstrel",
        "required": false
      },
      {
        "word": "Merry Andrew",
        "definition": "clown",
        "required": false
      },
      {
        "word": "quarterstaff",
        "definition": "a stout, iron-tipped staff, used as a weapon",
        "required": false
      },
      {
        "word": "aqua-vitae",
        "definition": "brandy",
        "required": false
      },
      {
        "word": "depredations",
        "definition": "acts of robbery evidence or plundering",
        "required": true
      },
      {
        "word": "probity",
        "definition": "integrity",
        "required": true
      },
      {
        "word": "unbenignantly",
        "definition": "unkindly",
        "required": false
      },
      {
        "word": "animadversion",
        "definition": "unfavorable comment; criticism",
        "required": false
      },
      {
        "word": "galliard",
        "definition": "lively",
        "required": false
      }
    ],
    "22": [
      {
        "word": "morions",
        "definition": "crested helmets",
        "required": false
      },
      {
        "word": "necromancy",
        "definition": "black magic; sorcery",
        "required": false
      },
      {
        "word": "indefatigable",
        "definition": "untiring",
        "required": false
      },
      {
        "word": "audacity",
        "definition": "bold daring; courage",
        "required": true
      }
    ],
    "23": [
      {
        "word": "oracles",
        "definition": "person believed to be speaking for a deity",
        "required": true
      },
      {
        "word": "transitory",
        "definition": "temporary; not enduring",
        "required": true
      },
      {
        "word": "eminence",
        "definition": "a high point",
        "required": false
      },
      {
        "word": "symphonious",
        "definition": "harmonious",
        "required": true
      },
      {
        "word": "apotheosized",
        "definition": "glorified; idealized",
        "required": true
      },
      {
        "word": "appalled",
        "definition": "filled with dismay; shocked",
        "required": true
      }
    ],
    "24": [
      {
        "word": "conjectural",
        "definition": "based on guesswork or incomplete evidence",
        "required": true
      },
      {
        "word": "nugatory",
        "definition": "worthless; trivial",
        "required": false
      },
      {
        "word": "escutcheon",
        "definition": "a shield on which a coat of arms is displayed",
        "required": false
      },
      {
        "word": "gules",
        "definition": "in heraldry, the color red",
        "required": false
      }
    ]
  }
}

/* -------- DOM Elements -------- */
const chapterSelect = document.getElementById("chapterSelect");
const defBox = document.getElementById("definitionBox");
const opts = document.getElementById("options");
const submitBtn = document.getElementById("submitBtn");
const nextBtn = document.getElementById("nextBtn");
const startBtn = document.getElementById("startBtn");
const explain = document.getElementById("explainBox");
const prevBox = document.getElementById("previousWord");
const seenBox = document.getElementById("seenList");
const scoreText = document.getElementById("scoreText");
const bar = document.getElementById("progressBar");

/* -------- Game State -------- */
let studyWords = [];
let pool = [];
let current = null;
let correctSet = new Set();
let seenSet = new Set();
let lastWord = null;

/* ----------------------------
   Build Chapter Selector
---------------------------- */
Object.keys(data.chapters).forEach(ch => {
  const label = document.createElement("label");
  label.innerHTML = `<input type="checkbox" value="${ch}"> Ch ${ch}`;
  chapterSelect.appendChild(label);
});

/* ----------------------------
         Start Quiz
---------------------------- */
startBtn.onclick = () => {
  const selected = [...chapterSelect.querySelectorAll("input:checked")].map(x => x.value);

  if (selected.length === 0) {
    alert("Select at least one chapter.");
    return;
  }

  const requiredOnly = document.getElementById("requiredOnly").checked;

  studyWords = [];
  selected.forEach(ch => {
    const chapterWords = data.chapters[ch];
    if (requiredOnly) {
      studyWords.push(...chapterWords.filter(w => w.required === true));
    } else {
      studyWords.push(...chapterWords);
    }
  });

  if (studyWords.length === 0) {
    alert("No words found with the current filter. Try unchecking 'Required Words Only'.");
    return;
  }

  pool = studyWords.slice();
  correctSet.clear();
  seenSet.clear();

  updateSidebar();
  updateScore();

  startBtn.style.display = "none";
  nextBtn.style.display = "none";
  submitBtn.style.display = "inline-block";

  nextQuestion();
};

/* ----------------------------
        Next Question
---------------------------- */
function nextQuestion() {
  explain.style.display = "none";
  opts.innerHTML = "";

  if (pool.length === 0) {
    defBox.textContent = "All Selected Words Mastered!";
    submitBtn.style.display = "none";
    nextBtn.style.display = "none";
    return;
  }

  current = pool[Math.floor(Math.random() * pool.length)];
  defBox.textContent = current.definition;

  const distractors = new Set();
  while (distractors.size < 3) {
    const rand = studyWords[Math.floor(Math.random() * studyWords.length)];
    if (rand.word !== current.word) distractors.add(rand.word);
  }

  const choices = [current.word, ...distractors].sort(() => Math.random() - 0.5);

  choices.forEach(choice => {
    const div = document.createElement("div");
    div.className = "option";
    div.textContent = choice;
    div.onclick = () => {
      document.querySelectorAll(".option").forEach(o => o.classList.remove("selected"));
      div.classList.add("selected");
    };
    opts.appendChild(div);
  });

  submitBtn.style.display = "inline-block";
  nextBtn.style.display = "none";
}

/* ----------------------------
           Submit
---------------------------- */
submitBtn.onclick = () => {
  const sel = document.querySelector(".option.selected");
  if (!sel) { alert("Choose an option first."); return; }

  const chosen = sel.textContent.trim();
  const correct = current.word;
  const isCorrect = chosen === correct;

  opts.querySelectorAll(".option").forEach(o => o.style.pointerEvents = "none");
  seenSet.add(current.word);
  lastWord = current;

  if (isCorrect) {
    explain.style.display = "block";
    explain.textContent = `✔ Correct → ${current.word}: ${current.definition}`;
    correctSet.add(current.word);
    pool = pool.filter(w => w.word !== current.word);
    updateScore();
  } else {
    explain.style.display = "block";
    explain.innerHTML = `✖ Incorrect → Correct: <b>${current.word}</b><br><br><b>Definitions:</b><br>`;
    
    document.querySelectorAll(".option").forEach(opt => {
      const w = studyWords.find(e => e.word === opt.textContent);
      if (w) explain.innerHTML += `<div><b>${w.word}</b>: ${w.definition}</div>`;
    });
  }

  updateSidebar();

  submitBtn.style.display = "none";
  nextBtn.style.display = "inline-block";
};

/* ----------------------------
           Utilities
---------------------------- */
function updateSidebar() {
  prevBox.innerHTML = lastWord
    ? `<b>${lastWord.word}</b>: ${lastWord.definition}`
    : "<small>None yet</small>";

  seenBox.innerHTML = "";
  seenSet.forEach(w => {
    const item = studyWords.find(e => e.word === w);
    if (item) seenBox.innerHTML += `<div><b>${item.word}</b>: ${item.definition}</div>`;
  });
}

function updateScore() {
  scoreText.textContent = `${correctSet.size} correct`;
  bar.style.width = (correctSet.size / studyWords.length) * 100 + "%";
}

nextBtn.onclick = nextQuestion;
</script>

</body>
</html>

</div>
