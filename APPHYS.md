---
permalink:/apphys
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AP Physics C: Unit 8</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Merriweather:wght@400;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            background: #fafbfc;
            color: #1a202c;
            line-height: 1.7;
        }

        .header {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: white;
            padding: 120px 40px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -10%;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(59, 130, 246, 0.1) 0%, transparent 70%);
            border-radius: 50%;
        }

        .header::after {
            content: '';
            position: absolute;
            bottom: -40%;
            left: -5%;
            width: 400px;
            height: 400px;
            background: radial-gradient(circle, rgba(139, 92, 246, 0.08) 0%, transparent 70%);
            border-radius: 50%;
        }

        .header-content {
            position: relative;
            z-index: 1;
        }

        .header h1 {
            font-size: 3.5em;
            font-weight: 700;
            margin-bottom: 15px;
            letter-spacing: -0.5px;
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
            font-weight: 300;
            letter-spacing: 0.3px;
        }

        .breadcrumb {
            font-size: 0.9em;
            opacity: 0.7;
            margin-top: 20px;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 280px 1fr;
            gap: 60px;
            padding: 60px 40px;
        }

        .sidebar {
            position: sticky;
            top: 40px;
            height: fit-content;
        }

        .sidebar-title {
            font-size: 0.85em;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1.2px;
            color: #64748b;
            margin-bottom: 25px;
            display: block;
        }

        .sidebar-nav {
            list-style: none;
        }

        .sidebar-nav li {
            margin-bottom: 0;
        }

        .sidebar-nav a {
            display: block;
            padding: 12px 16px;
            color: #475569;
            text-decoration: none;
            font-size: 0.95em;
            font-weight: 400;
            border-radius: 8px;
            transition: all 0.25s ease;
            border-left: 3px solid transparent;
        }

        .sidebar-nav a:hover {
            background: #f1f5f9;
            color: #0f172a;
            border-left-color: #3b82f6;
            transform: translateX(4px);
        }

        .main {
            display: flex;
            flex-direction: column;
            gap: 80px;
        }

        section {
            scroll-margin-top: 100px;
        }

        .section-header {
            margin-bottom: 40px;
        }

        .section-number {
            font-size: 3em;
            font-weight: 700;
            background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
        }

        h2 {
            font-size: 2.5em;
            font-weight: 700;
            color: #0f172a;
            margin-bottom: 10px;
            letter-spacing: -0.3px;
        }

        h3 {
            font-size: 1.6em;
            font-weight: 600;
            color: #0f172a;
            margin-top: 45px;
            margin-bottom: 20px;
            letter-spacing: -0.2px;
        }

        h4 {
            font-size: 1.1em;
            font-weight: 600;
            color: #1e293b;
            margin-top: 20px;
            margin-bottom: 12px;
        }

        .subsection-text {
            color: #64748b;
            font-size: 0.95em;
            margin-top: 5px;
            font-weight: 500;
        }

        p {
            margin-bottom: 16px;
            color: #475569;
            font-size: 1em;
        }

        ul, ol {
            margin-left: 24px;
            margin-bottom: 20px;
        }

        li {
            margin-bottom: 10px;
            color: #475569;
        }

        .equation-box {
            background: #f8fafc;
            border: 1px solid #e2e8f0;
            padding: 28px 32px;
            border-radius: 12px;
            margin: 28px 0;
            font-family: 'Courier New', monospace;
            font-size: 1.05em;
            line-height: 1.9;
            color: #1e293b;
            box-shadow: 0 2px 8px rgba(15, 23, 42, 0.04);
            transition: all 0.3s ease;
        }

        .equation-box:hover {
            box-shadow: 0 4px 16px rgba(15, 23, 42, 0.08);
            border-color: #cbd5e1;
        }

        .concept {
            background: linear-gradient(135deg, #eff6ff 0%, #f0f9ff 100%);
            border-left: 4px solid #3b82f6;
            padding: 20px 24px;
            border-radius: 10px;
            margin: 24px 0;
            color: #1e40af;
        }

        .warning {
            background: linear-gradient(135deg, #fef2f2 0%, #fef5f5 100%);
            border-left: 4px solid #ef4444;
            padding: 20px 24px;
            border-radius: 10px;
            margin: 24px 0;
            color: #991b1b;
        }

        .key-point {
            background: linear-gradient(135deg, #faf5ff 0%, #fdf2f8 100%);
            border-left: 4px solid #a855f7;
            padding: 20px 24px;
            border-radius: 10px;
            margin: 24px 0;
            color: #6d28d9;
        }

        .grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 28px;
            margin: 28px 0;
        }

        .card {
            background: white;
            border: 1px solid #e2e8f0;
            border-radius: 12px;
            padding: 28px;
            transition: all 0.3s ease;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
        }

        .card:hover {
            border-color: #cbd5e1;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
            transform: translateY(-2px);
        }

        .card h4 {
            color: #0f172a;
            margin-top: 0;
            font-size: 1.15em;
        }

        .card p {
            font-size: 0.95em;
            margin-bottom: 12px;
        }

        .card ul {
            margin-left: 20px;
        }

        .card li {
            font-size: 0.95em;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 32px 0;
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
            border: 1px solid #e2e8f0;
        }

        th {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: white;
            padding: 18px 20px;
            text-align: left;
            font-weight: 600;
            font-size: 0.95em;
            letter-spacing: 0.3px;
        }

        td {
            padding: 16px 20px;
            border-bottom: 1px solid #e2e8f0;
            font-size: 0.95em;
            color: #475569;
        }

        tr:last-child td {
            border-bottom: none;
        }

        tr:hover {
            background: #f8fafc;
        }

        .comparison {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
            margin: 28px 0;
        }

        .comparison-item {
            background: white;
            border: 1px solid #e2e8f0;
            border-radius: 12px;
            padding: 24px;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
        }

        .comparison-item h4 {
            color: #0f172a;
            margin-top: 0;
            font-size: 1.1em;
            margin-bottom: 12px;
        }

        .comparison-item p {
            font-size: 0.95em;
            color: #475569;
        }

        .checklist {
            list-style: none;
            margin-left: 0;
        }

        .checklist li {
            padding: 10px 0 10px 30px;
            position: relative;
            margin-bottom: 8px;
        }

        .checklist li::before {
            content: "✓";
            position: absolute;
            left: 0;
            color: #059669;
            font-weight: 700;
            font-size: 1.1em;
        }

        .mistake {
            background: white;
            border-left: 4px solid #dc2626;
            padding: 20px 24px;
            margin: 20px 0;
            border-radius: 10px;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
        }

        .mistake strong {
            color: #7f1d1d;
        }

        .mistake p {
            margin-bottom: 8px;
            font-size: 0.95em;
        }

        footer {
            background: #0f172a;
            color: white;
            text-align: center;
            padding: 60px 40px;
            margin-top: 80px;
        }

        footer h3 {
            color: white;
            margin-top: 0;
            font-size: 1.3em;
        }

        footer p {
            color: #cbd5e1;
            margin-bottom: 8px;
        }

        .back-to-top {
            position: fixed;
            bottom: 40px;
            right: 40px;
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
            color: white;
            border: none;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2em;
            opacity: 0;
            transition: all 0.3s ease;
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.4);
            pointer-events: none;
        }

        .back-to-top:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(59, 130, 246, 0.5);
        }

        .back-to-top.show {
            opacity: 1;
            pointer-events: auto;
        }

        @media (max-width: 1024px) {
            .container {
                grid-template-columns: 1fr;
                gap: 40px;
                padding: 40px 30px;
            }

            .sidebar {
                position: relative;
                top: 0;
            }

            .sidebar-nav a {
                display: inline-block;
                margin-right: 12px;
                margin-bottom: 8px;
            }

            .grid, .comparison {
                grid-template-columns: 1fr;
            }

            h2 {
                font-size: 2em;
            }

            h3 {
                font-size: 1.4em;
            }

            .header h1 {
                font-size: 2.5em;
            }
        }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, #cbd5e1, transparent);
            margin: 60px 0;
        }

        .section-intro {
            font-size: 1.05em;
            color: #475569;
            margin-bottom: 30px;
            line-height: 1.8;
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="header-content">
            <h1>AP Physics C</h1>
            <p>Unit 8: Charge, Fields & Gauss's Law</p>
            <span class="breadcrumb">Electrostatics & Electromagnetic Theory</span>
        </div>
    </div>

    <div class="container">
        <aside class="sidebar">
            <strong class="sidebar-title">Contents</strong>
            <ul class="sidebar-nav">
                <li><a href="#section1">Electric Charge</a></li>
                <li><a href="#section2">Coulomb's Law</a></li>
                <li><a href="#section3">Electric Fields</a></li>
                <li><a href="#section4">Electric Flux</a></li>
                <li><a href="#section5">Gauss's Law</a></li>
                <li><a href="#section6">Applications</a></li>
                <li><a href="#section7">Conductors</a></li>
                <li><a href="#section8">Strategies</a></li>
                <li><a href="#section9">Equations</a></li>
                <li><a href="#section10">Common Mistakes</a></li>
            </ul>
        </aside>

        <main class="main">
            <!-- SECTION 1 -->
            <section id="section1">
                <div class="section-header">
                    <span class="section-number">1</span>
                    <h2>Electric Charge</h2>
                    <p class="subsection-text">Fundamental properties and charge distribution</p>
                </div>

                <p class="section-intro">Charge is a fundamental property of matter, measured in Coulombs (C). All matter contains two types of charge that interact through electromagnetic forces.</p>

                <h3>What is Charge?</h3>
                <ul>
                    <li>Fundamental property of matter (analogous to mass)</li>
                    <li>Two types: <strong>positive</strong> (protons) and <strong>negative</strong> (electrons)</li>
                    <li>Elementary charge: <strong>e = 1.60 × 10⁻¹⁹ C</strong></li>
                    <li>Charge is quantized and conserved</li>
                </ul>

                <div class="key-point">
                    <strong>Key Principle:</strong> Charge is always transferred by the flow of electrons. A positive charge represents an electron deficit.
                </div>

                <h3>Conductors vs Insulators</h3>
                <div class="grid">
                    <div class="card">
                        <h4>Conductors</h4>
                        <p>Materials with free electrons that move easily through the material.</p>
                        <ul>
                            <li>Charge transfers readily</li>
                            <li>Examples: copper, aluminum, silver</li>
                            <li>Used in: wires, circuits, electrodes</li>
                        </ul>
                    </div>
                    <div class="card">
                        <h4>Insulators</h4>
                        <p>Materials where electrons are tightly bound to nuclei.</p>
                        <ul>
                            <li>Charge does not transfer</li>
                            <li>Examples: glass, rubber, plastic</li>
                            <li>Used in: protection, isolation</li>
                        </ul>
                    </div>
                </div>

                <h3>Charge Density Notation</h3>
                <p>When charge is distributed over a region, we use density to describe it:</p>
                <div class="equation-box">
                    <strong>Linear Charge Density:</strong> λ = Q/L (units: C/m)<br>
                    dq = λ · ds<br><br>
                    <strong>Surface Charge Density:</strong> σ = Q/A (units: C/m²)<br>
                    dq = σ · dA<br><br>
                    <strong>Volume Charge Density:</strong> ρ = Q/V (units: C/m³)<br>
                    dq = ρ · dV
                </div>

                <div class="concept">
                    <strong>Important Example:</strong> For a small arc element of a ring with radius R, angle dθ, and linear charge density λ:<br><br>
                    ds = R dθ  →  <strong>dq = λR dθ</strong>
                </div>
            </section>

            <div class="divider"></div>

            <!-- SECTION 2 -->
            <section id="section2">
                <div class="section-header">
                    <span class="section-number">2</span>
                    <h2>Coulomb's Law</h2>
                    <p class="subsection-text">The force between charged objects</p>
                </div>

                <p class="section-intro">Coulomb's Law describes the electrostatic force between two point charges, forming the foundation of electrostatics.</p>

                <h3>The Law</h3>
                <div class="equation-box">
                    <strong>F = k|Q₁Q₂|/r²</strong><br><br>
                    where:<br>
                    • k = 8.99 × 10⁹ N·m²/C² (Coulomb's constant)<br>
                    • r = distance between charges<br>
                    • F = magnitude of force (Newtons)
                </div>

                <h3>Direction of Force</h3>
                <div class="comparison">
                    <div class="comparison-item">
                        <h4>Like Charges</h4>
                        <p><strong>Repulsion:</strong> Force points away from the other charge</p>
                        <p style="font-size: 0.9em; opacity: 0.7; margin-top: 12px;">Same sign charges push each other apart</p>
                    </div>
                    <div class="comparison-item">
                        <h4>Opposite Charges</h4>
                        <p><strong>Attraction:</strong> Force points toward the other charge</p>
                        <p style="font-size: 0.9em; opacity: 0.7; margin-top: 12px;">Different signs pull each other together</p>
                    </div>
                </div>

                <h3>Superposition Principle</h3>
                <div class="concept">
                    The net force on a charge is the vector sum of forces from all other charges present.
                </div>

                <div class="equation-box">
                    <strong>F⃗<sub>net</sub> = F⃗₁ + F⃗₂ + F⃗₃ + ... = ΣF⃗ᵢ</strong>
                </div>

                <h3>Problem-Solving Approach</h3>
                <ol>
                    <li>Calculate force from each charge separately (magnitude and direction)</li>
                    <li>Resolve forces into x and y components</li>
                    <li>Sum all x-components: F<sub>x</sub> = ΣF<sub>ix</sub></li>
                    <li>Sum all y-components: F<sub>y</sub> = ΣF<sub>iy</sub></li>
                    <li>Find resultant magnitude: F = √(F<sub>x</sub>² + F<sub>y</sub>²)</li>
                    <li>Find direction: θ = arctan(F<sub>y</sub>/F<sub>x</sub>)</li>
                </ol>
            </section>

            <div class="divider"></div>

            <!-- SECTION 3 -->
            <section id="section3">
                <div class="section-header">
                    <span class="section-number">3</span>
                    <h2>Electric Fields</h2>
                    <p class="subsection-text">How charges create fields that affect other charges</p>
                </div>

                <p class="section-intro">An electric field represents the influence of a charge on the space around it, independent of any test charge placed there.</p>

                <h3>Definition</h3>
                <div class="equation-box">
                    <strong>E = F/q = kQ/r²</strong><br><br>
                    Units: N/C (Newtons per Coulomb) or V/m (Volts per meter)
                </div>

                <div class="concept">
                    Electric field is the force per unit charge that would be exerted on a positive test charge placed at that location.
                </div>

                <h3>Field Direction</h3>
                <div class="comparison">
                    <div class="comparison-item">
                        <h4>Positive Source Charge</h4>
                        <p>Field points <strong>radially outward</strong> from the charge</p>
                        <p style="font-size: 0.9em; color: #475569;">Repels positive test charges</p>
                    </div>
                    <div class="comparison-item">
                        <h4>Negative Source Charge</h4>
                        <p>Field points <strong>radially inward</strong> toward the charge</p>
                        <p style="font-size: 0.9em; color: #475569;">Attracts positive test charges</p>
                    </div>
                </div>

                <h3>Superposition of Fields</h3>
                <div class="equation-box">
                    <strong>E⃗<sub>total</sub> = E⃗₁ + E⃗₂ + E⃗₃ + ... = ΣE⃗ᵢ</strong>
                </div>

                <h3>Common Field Configurations</h3>
                <table>
                    <tr>
                        <th>Configuration</th>
                        <th>Formula</th>
                        <th>Key Feature</th>
                    </tr>
                    <tr>
                        <td>Point Charge</td>
                        <td>E = kQ/r²</td>
                        <td>1/r² dependence</td>
                    </tr>
                    <tr>
                        <td>Ring (on axis)</td>
                        <td>E = kQx/(R² + x²)^(3/2)</td>
                        <td>Maximum at center edge</td>
                    </tr>
                    <tr>
                        <td>Disk (on axis)</td>
                        <td>E = (σ/2ε₀)[1 - x/√(R² + x²)]</td>
                        <td>Approaches σ/2ε₀</td>
                    </tr>
                    <tr>
                        <td>Infinite Line</td>
                        <td>E = λ/(2πε₀r)</td>
                        <td>⚠️ 1/r (not 1/r²!)</td>
                    </tr>
                    <tr>
                        <td>Infinite Plane</td>
                        <td>E = σ/(2ε₀)</td>
                        <td>⚠️ Constant (independent of distance!)</td>
                    </tr>
                </table>
            </section>

            <div class="divider"></div>

            <!-- SECTION 4 -->
            <section id="section4">
                <div class="section-header">
                    <span class="section-number">4</span>
                    <h2>Electric Flux</h2>
                    <p class="subsection-text">Measuring field penetration through surfaces</p>
                </div>

                <p class="section-intro">Electric flux quantifies how much electric field passes through a given surface, serving as a bridge to Gauss's Law.</p>

                <h3>Definition</h3>
                <div class="equation-box">
                    <strong>Φ = ∫ E⃗ · dA⃗</strong><br><br>
                    For uniform field: <strong>Φ = EA cos θ</strong>
                </div>

                <h3>Flux Interpretation</h3>
                <table>
                    <tr>
                        <th>Condition</th>
                        <th>Flux Value</th>
                        <th>Interpretation</th>
                    </tr>
                    <tr>
                        <td>E perpendicular to surface (θ = 0°)</td>
                        <td>Φ = EA</td>
                        <td>Maximum flux, field perpendicular</td>
                    </tr>
                    <tr>
                        <td>E parallel to surface (θ = 90°)</td>
                        <td>Φ = 0</td>
                        <td>No flux, field grazes surface</td>
                    </tr>
                    <tr>
                        <td>E points into surface (θ = 180°)</td>
                        <td>Φ = -EA</td>
                        <td>Negative flux, inward field</td>
                    </tr>
                </table>

                <div class="key-point">
                    <strong>Critical Insight for Closed Surfaces:</strong> If no charge is enclosed by the surface, the net flux equals zero because all field lines that enter must also exit.
                </div>
            </section>

            <div class="divider"></div>

            <!-- SECTION 5 -->
            <section id="section5">
                <div class="section-header">
                    <span class="section-number">5</span>
                    <h2>Gauss's Law</h2>
                    <p class="subsection-text">The foundation of electrostatics</p>
                </div>

                <p class="section-intro">Gauss's Law is one of Maxwell's four fundamental equations. It elegantly relates the charge distribution to the resulting electric field.</p>

                <h3>The Law</h3>
                <div class="equation-box" style="background: linear-gradient(135deg, #faf5ff 0%, #fdf2f8 100%); border-left-color: #d946ef;">
                    <strong style="font-size: 1.2em; color: #6d28d9;">∮ E⃗ · dA⃗ = Q<sub>enc</sub> / ε₀</strong><br><br>
                    where ε₀ = 8.854 × 10⁻¹² C²/(N·m²)
                </div>

                <div class="concept">
                    The total electric flux through any closed surface equals the enclosed charge divided by the permittivity of free space. The surface can be any shape—it's merely a mathematical construct.
                </div>

                <h3>Why Gauss's Law is Powerful</h3>
                <ul>
                    <li>One of Maxwell's four fundamental equations of electromagnetism</li>
                    <li>Flux depends only on enclosed charge—external charges don't matter</li>
                    <li>With high symmetry, the integral becomes trivial to evaluate</li>
                    <li>Often simpler than integration using Coulomb's Law</li>
                </ul>

                <h3>Symmetry Types</h3>
                <table>
                    <tr>
                        <th>Symmetry Type</th>
                        <th>Gaussian Surface</th>
                        <th>Flux Integral</th>
                    </tr>
                    <tr>
                        <td><strong>Spherical</strong></td>
                        <td>Concentric sphere, radius r</td>
                        <td>E · 4πr²</td>
                    </tr>
                    <tr>
                        <td><strong>Cylindrical</strong></td>
                        <td>Coaxial cylinder, radius r, length L</td>
                        <td>E · 2πrL</td>
                    </tr>
                    <tr>
                        <td><strong>Planar</strong></td>
                        <td>Pillbox perpendicular to plane</td>
                        <td>2EA</td>
                    </tr>
                </table>

                <div class="warning">
                    <strong>Critical Requirement:</strong> The electric field must be constant in magnitude on the part of the Gaussian surface where you calculate the flux. Identifying the correct symmetry is the key to solving these problems.
                </div>
            </section>

            <div class="divider"></div>

            <!-- SECTION 6 -->
            <section id="section6">
                <div class="section-header">
                    <span class="section-number">6</span>
                    <h2>Applications of Gauss's Law</h2>
                    <p class="subsection-text">Solving real-world configurations</p>
                </div>

                <p class="section-intro">Gauss's Law simplifies field calculations for highly symmetric charge distributions that would be tedious to solve using Coulomb's Law.</p>

                <h3>Infinite Charged Plane</h3>
                <div class="card">
                    <h4>Configuration</h4>
                    <p>Infinite plane with uniform surface charge density σ</p>
                    <div class="equation-box">
                        <strong>E = σ/(2ε₀)</strong>
                    </div>
                    <p><strong>Remarkable Result:</strong> The field is independent of distance from the plane!</p>
                </div>

                <h3>Parallel Plate Capacitor</h3>
                <div class="comparison">
                    <div class="comparison-item">
                        <h4>Between Plates</h4>
                        <p>Electric fields from both plates add (same direction):</p>
                        <div class="equation-box">
                            E = σ/ε₀
                        </div>
                    </div>
                    <div class="comparison-item">
                        <h4>Outside Plates</h4>
                        <p>Electric fields cancel (opposite directions):</p>
                        <div class="equation-box">
                            E = 0
                        </div>
                    </div>
                </div>

                <h3>Uniformly Charged Sphere (Insulator)</h3>
                <table>
                    <tr>
                        <th>Region</th>
                        <th>Electric Field</th>
                        <th>Characteristics</th>
                    </tr>
                    <tr>
                        <td>Inside (r &lt; R)</td>
                        <td>E = Qr/(4πε₀R³)</td>
                        <td>Linear increase with r; E = 0 at center</td>
                    </tr>
                    <tr>
                        <td>Outside (r &gt; R)</td>
                        <td>E = Q/(4πε₀r²)</td>
                        <td>1/r² decrease; identical to point charge</td>
                    </tr>
                </table>

                <h3>Hollow Conducting Sphere</h3>
                <table>
                    <tr>
                        <th>Region</th>
                        <th>Electric Field</th>
                        <th>Explanation</th>
                    </tr>
                    <tr>
                        <td>Inside (r &lt; R)</td>
                        <td>E = 0</td>
                        <td>Q<sub>enc</sub> = 0 (all charge on shell)</td>
                    </tr>
                    <tr>
                        <td>Outside (r &gt; R)</td>
                        <td>E = Q/(4πε₀r²)</td>
                        <td>Behaves like a point charge</td>
                    </tr>
                </table>

                <h3>Infinite Line Charge</h3>
                <div class="card">
                    <h4>Configuration</h4>
                    <p>Infinitely long wire with uniform linear charge density λ at distance r from the axis</p>
                    <div class="equation-box">
                        E = λ/(2πε₀r)
                    </div>
                    <p><strong>⚠️ Important:</strong> Note the 1/r dependence, not 1/r². This is distinctly different from point charges!</p>
                </div>
            </section>

            <div class="divider"></div>

            <!-- SECTION 7 -->
            <section id="section7">
                <div class="section-header">
                    <span class="section-number">7</span>
                    <h2>Conductors</h2>
                    <p class="subsection-text">Charge behavior in conductive materials</p>
                </div>

                <p class="section-intro">Conductors respond to electric fields by allowing their free charges to move. Understanding conductor behavior is essential for practical circuit applications.</p>

                <h3>Fundamental Properties (Electrostatic Equilibrium)</h3>
                <div class="grid">
                    <div class="card">
                        <h4>E = 0 Inside</h4>
                        <p>Charges rearrange until the internal field vanishes completely.</p>
                    </div>
                    <div class="card">
                        <h4>Charge on Surface</h4>
                        <p>All excess charge resides on the outer surface, none within the material.</p>
                    </div>
                    <div class="card">
                        <h4>E Perpendicular</h4>
                        <p>Just outside the surface, E is perpendicular: E = σ/ε₀</p>
                    </div>
                    <div class="card">
                        <h4>Electrostatic Shielding</h4>
                        <p>Internal cavities are shielded from external electric fields (Faraday cage effect).</p>
                    </div>
                </div>

                <div class="key-point">
                    <strong>In electrostatic equilibrium:</strong> All free charges in a conductor have stopped moving. No force acts on them. The electric field inside must be zero.
                </div>

                <h3>Grounding</h3>
                <div class="concept">
                    <strong>Ground Definition:</strong> An electrical connection to Earth, which acts as an essentially infinite reservoir of charge.<br><br>
                    When a conductor is grounded, charge flows to or from Earth until the conductor's potential equals Earth's reference potential (0V).
                </div>
            </section>

            <div class="divider"></div>

            <!-- SECTION 8 -->
            <section id="section8">
                <div class="section-header">
                    <span class="section-number">8</span>
                    <h2>Problem-Solving Strategies</h2>
                    <p class="subsection-text">Choosing the right approach</p>
                </div>

                <h3>Use Coulomb's Law When:</h3>
                <ul>
                    <li>You have discrete point charges</li>
                    <li>You need to calculate force directly</li>
                    <li>The charge distribution has no obvious symmetry</li>
                </ul>

                <h3>Use Electric Field When:</h3>
                <ul>
                    <li>Finding the field at a specific point</li>
                    <li>Dealing with multiple charges or continuous distributions</li>
                    <li>You need to use superposition</li>
                </ul>

                <h3>Use Gauss's Law When:</h3>
                <div class="key-point">
                    ✓ HIGH symmetry is present (spherical, cylindrical, or planar)<br>
                    ✓ Finding E from a charge distribution<br>
                    ✓ Working with conductors<br>
                    ✓ Integration using Coulomb's Law would be complicated
                </div>

                <h3>Gauss's Law Step-by-Step</h3>
                <ol style="background: #f8fafc; padding: 24px 32px; border-radius: 12px; border: 1px solid #e2e8f0;">
                    <li><strong>Identify Symmetry:</strong> Is it spherical, cylindrical, or planar?</li>
                    <li><strong>Choose Gaussian Surface:</strong> Match the symmetry of the charge distribution</li>
                    <li><strong>Find Q<sub>enc</sub>:</strong> Determine the charge enclosed by your surface</li>
                    <li><strong>Calculate Flux:</strong> Identify which surfaces contribute to ∮ E⃗ · dA⃗</li>
                    <li><strong>Apply Gauss's Law:</strong> ∮ E⃗ · dA⃗ = Q<sub>enc</sub>/ε₀</li>
                    <li><strong>Solve for E:</strong> Algebraic manipulation</li>
                    <li><strong>Verify:</strong> Check units, signs, and limiting cases</li>
                </ol>
            </section>

            <div class="divider"></div>

            <!-- SECTION 9 -->
            <section id="section9">
                <div class="section-header">
                    <span class="section-number">9</span>
                    <h2>Essential Equations</h2>
                    <p class="subsection-text">Complete reference for all key formulas</p>
                </div>

                <h3>Fundamental Constants</h3>
                <div class="equation-box">
                    k = 8.99 × 10⁹ N·m²/C² (Coulomb's constant)<br>
                    ε₀ = 8.854 × 10⁻¹² C²/(N·m²) (Permittivity)<br>
                    e = 1.60 × 10⁻¹⁹ C (Elementary charge)
                </div>

                <h3>Charge Density Definitions</h3>
                <table>
                    <tr>
                        <th>Quantity</th>
                        <th>Symbol</th>
                        <th>Definition</th>
                        <th>Units</th>
                    </tr>
                    <tr>
                        <td>Linear charge density</td>
                        <td>λ</td>
                        <td>Q/L</td>
                        <td>C/m</td>
                    </tr>
                    <tr>
                        <td>Surface charge density</td>
                        <td>σ</td>
                        <td>Q/A</td>
                        <td>C/m²</td>
                    </tr>
                    <tr>
                        <td>Volume charge density</td>
                        <td>ρ</td>
                        <td>Q/V</td>
                        <td>C/m³</td>
                    </tr>
                </table>

                <h3>Core Equations</h3>
                <div class="equation-box">
                    <strong>Coulomb's Law:</strong> F = k|Q₁Q₂|/r²<br><br>
                    <strong>Electric Field:</strong> E = F/q = k|Q|/r²<br><br>
                    <strong>Electric Flux:</strong> Φ = EA cos θ<br><br>
                    <strong>Gauss's Law:</strong> ∮ E⃗ · dA⃗ = Q<sub>enc</sub>/ε₀
                </div>

                <h3>Field Magnitudes Reference Table</h3>
                <table>
                    <tr>
                        <th>Configuration</th>
                        <th>Formula</th>
                        <th>Domain</th>
                    </tr>
                    <tr>
                        <td>Point charge</td>
                        <td>E = kQ/r²</td>
                        <td>r > 0</td>
                    </tr>
                    <tr>
                        <td>Solid sphere (uniform)</td>
                        <td>E = Qr/(4πε₀R³)</td>
                        <td>r &lt; R</td>
                    </tr>
                    <tr>
                        <td>Solid sphere (uniform)</td>
                        <td>E = Q/(4πε₀r²)</td>
                        <td>r &gt; R</td>
                    </tr>
                    <tr>
                        <td>Spherical shell</td>
                        <td>E = 0</td>
                        <td>r &lt; R</td>
                    </tr>
                    <tr>
                        <td>Spherical shell</td>
                        <td>E = Q/(4πε₀r²)</td>
                        <td>r &gt; R</td>
                    </tr>
                    <tr>
                        <td>Infinite line charge</td>
                        <td>E = λ/(2πε₀r)</td>
                        <td>All r</td>
                    </tr>
                    <tr>
                        <td>Infinite plane</td>
                        <td>E = σ/(2ε₀)</td>
                        <td>All distances</td>
                    </tr>
                    <tr>
                        <td>Parallel plates (between)</td>
                        <td>E = σ/ε₀</td>
                        <td>Interior</td>
                    </tr>
                </table>
            </section>

            <div class="divider"></div>

            <!-- SECTION 10 -->
            <section id="section10">
                <div class="section-header">
                    <span class="section-number">10</span>
                    <h2>Common Mistakes</h2>
                    <p class="subsection-text">Pitfalls to avoid on exams</p>
                </div>

                <div class="mistake">
                    <strong>❌ Mistake 1: Omitting the differential in charge elements</strong><br>
                    <p><strong>Wrong:</strong> dq = λ</p>
                    <p><strong>Correct:</strong> dq = λ · ds</p>
                    <p>The differential is essential to establish proper units and relationships.</p>
                </div>

                <div class="mistake">
                    <strong>❌ Mistake 2: Using total charge instead of enclosed charge</strong><br>
                    <p><strong>Remember:</strong> Gauss's Law uses only Q<sub>enc</sub>, the charge inside your Gaussian surface.</p>
                    <p>External charges don't contribute to the flux.</p>
                </div>

                <div class="mistake">
                    <strong>❌ Mistake 3: Assuming all configurations have 1/r² fields</strong><br>
                    <p><strong>Remember:</strong> Line charges produce 1/r fields, and infinite planes produce constant fields.</p>
                    <p>Only point charges and spherical symmetries yield 1/r² dependence.</p>
                </div>

                <div class="mistake">
                    <strong>❌ Mistake 4: Forgetting that E = 0 inside conductors</strong><br>
                    <p><strong>Always true:</strong> E = 0 everywhere inside a conductor in electrostatic equilibrium.</p>
                    <p>This is exact, not approximate.</p>
                </div>

                <div class="mistake">
                    <strong>❌ Mistake 5: Choosing the wrong Gaussian surface</strong><br>
                    <p><strong>Match symmetry:</strong> Spherical problem → spherical surface; Cylindrical → cylindrical; Planar → pillbox</p>
                    <p>Wrong surface makes the problem intractable.</p>
                </div>

                <h3>Things to Remember</h3>
                <ul class="checklist">
                    <li>Symmetry is the key to using Gauss's Law effectively</li>
                    <li>Always include charge density and the differential element: dq = density × element</li>
                    <li>E = 0 inside conductors in electrostatic equilibrium</li>
                    <li>Use enclosed charge only in Gauss's Law</li>
                    <li>Add fields and forces as vectors (components matter)</li>
                    <li>Never omit units and physical constants in final answers</li>
                    <li>Check your answer against limiting cases and physical intuition</li>
                </ul>

                <h3>Exam Confidence Checklist</h3>
                <div style="background: #f8fafc; padding: 24px; border-radius: 12px; border: 1px solid #e2e8f0;">
                    <p style="margin-bottom: 16px;"><strong>Before submitting your answer:</strong></p>
                    <ul class="checklist">
                        <li>Do my units make sense? [N/C for fields, N for forces]</li>
                        <li>Does the sign/direction make physical sense?</li>
                        <li>Do limiting cases work out correctly?</li>
                        <li>Have I included all necessary constants?</li>
                        <li>Did I answer the question that was asked?</li>
                    </ul>
                </div>
            </section>
        </main>
    </div>

    <footer>
        <h3>AP Physics C: Unit 8</h3>
        <p>Electrostatics & Electromagnetic Theory</p>
        <p style="font-size: 0.9em; margin-top: 20px;">Master the fundamental concepts of charge, fields, and Gauss's Law</p>
    </footer>

    <button class="back-to-top" id="backToTop">↑</button>

    <script>
        const backToTopBtn = document.getElementById('backToTop');

        window.addEventListener('scroll', () => {
            if (window.pageYOffset > 300) {
                backToTopBtn.classList.add('show');
            } else {
                backToTopBtn.classList.remove('show');
            }
        });

        backToTopBtn.addEventListener('click', () => {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        });

        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });
    </script>
</body>
</html>
