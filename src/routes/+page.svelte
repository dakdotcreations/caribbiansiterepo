<script>
	import { onMount } from "svelte"
	import gsap from "gsap"
	import { ScrollTrigger } from "gsap/dist/ScrollTrigger"
	import {
		Zap,
		Building2,
		HardHat,
		ShieldCheck,
		ArrowUpRight,
		FileText,
		ChevronRight,
		Download,
		CircleCheck,
		Truck,
		Users,
		Layers,
		Award,
		Briefcase,
		Upload,
		Calendar,
		Gauge,
	} from "@lucide/svelte"
	import { useGsap } from "$lib/utils/useGsap"

	// State management for interactive project showcase tabs
	let activeTab = $state("all")

	const projects = $state([
		{
			id: 1,
			title: "Kigali-Gisenyi Commercial Grid Integration",
			category: "electrical",
			categoryLabel: "Industrial Electrical",
			location: "Northern Hub Sector",
			year: "2025",
			metrics: {
				primary: "33kV / 11kV",
				secondary: "2x 15MVA Transformers",
				scale: "Regional Grid",
			},
			image: "Power_substation.jpeg", // Logo / Technical graphic
			description:
				"Complete design, installation, and commissioning of heavy step-down transformers and backup synchronized generator plants for high-load commercial facilities.",
		},
		{
			id: 2,
			title: "Commercial Center & Operations Tower",
			category: "construction",
			categoryLabel: "Commercial Construction",
			location: "Central Business District",
			year: "2024",
			metrics: {
				primary: "8-Story Structure",
				secondary: "Structural Reinforced Concrete",
				scale: "14,500 m²",
			},
			image: "Commercial_center.jpeg", // Team photo on rooftop site
			description:
				"Turnkey structural concrete erection, high-rise framing, curtain wall integration, and interior mechanical & electrical systems fit-out.",
		},
		{
			id: 3,
			title: "Industrial Bypass & Civil Arterial Roadway",
			category: "civil",
			categoryLabel: "Civil Engineering",
			location: "Eastern Transport Corridor",
			year: "2024",
			metrics: {
				primary: "28 KM Heavy Paving",
				secondary: "8,200 m³ Concrete",
				scale: "Class-A Highway",
			},
			image: "Highway_bypass.jpeg", // Site engineers in PPE on bridge deck
			description:
				"Comprehensive earthworks, site leveling, heavy asphalt surfacing, reinforced retaining walls, and municipal storm drainage networks.",
		},
	])

	let filteredProjects = $derived(
        activeTab === 'all'
            ? projects
            : projects.filter((p) => p.category === activeTab)
        );

	useGsap(() => {
		// Hero Text Staggered Reveal
		gsap.from(".gsap-hero-title", {
			y: 60,
			opacity: 0,
			duration: 1.2,
			stagger: 0.2,
			ease: "power3.out",
		})

		gsap.from(".gsap-hero-sub", {
			y: 30,
			opacity: 0,
			duration: 1,
			delay: 0.6,
			ease: "power2.out",
		})

		// Stats Section Scroll Trigger
		gsap.from(".gsap-stat-card", {
			scrollTrigger: {
				trigger: "#stats-bar",
				start: "top 85%",
			},
			y: 40,
			opacity: 0,
			duration: 0.8,
			stagger: 0.15,
			ease: "back.out(1.4)",
		})

        gsap.from('.gsap-service-card', {
            opacity: 0,
            y: 200,
            duration: 0.8,
            stagger: 0.2,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: '#services',
                start: 'top 85%',
                end: 'top top',
                // toggleActions: 'play none none reverse',
                scrub: 1
            }
        })

        gsap.from('.gsap-project-card', {
            opacity: 0,
            y: 200,
            duration: 0.8,
            stagger: 0.2,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: '#projects',
                start: 'top 85%',
                end: 'top top',
                // toggleActions: 'play none none reverse',
                scrub: 1
            }
        })

		// Safety Banner Reveal
		gsap.from(".gsap-safety-content", {
			scrollTrigger: {
				trigger: "#safety",
				start: "top 80%",
			},
			x: -50,
			opacity: 0,
			duration: 1,
			ease: "power3.out",
		})
	})
</script>

<!-- =================================================================== -->
<!-- HERO SECTION: High-Impact Corporate Enterprise Statement -->
<!-- =================================================================== -->
<section class="relative bg-foreground text-background pt-16 pb-32 overflow-hidden bg-blueprint border-b-8 border-primary">
	<!-- Architectural Accent Backdrop Elements -->
	<div class="absolute top-0 right-0 w-1/2 h-full bg-primary/10 -skew-x-12 translate-x-32 pointer-events-none hidden lg:block">
	</div>
	<div class="absolute bottom-0 right-10 w-96 h-96 bg-primary/5 rounded-full blur-3xl pointer-events-none">
	</div>

	<div class="container mx-auto px-6 relative z-10">
		<div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
			<!-- Main Text Block -->
			<div class="lg:col-span-8 space-y-8">
				<div class="inline-flex items-center gap-3 bg-white/10 backdrop-blur-md px-4 py-2 border border-white/20 text-primary text-xs uppercase">
					<HardHat class="w-4 h-4 text-primary" />
					<span>Commercial Contractor & Industrial Engineering Firm</span>
				</div>

				<h1 class="space-y-2">
					<div class="gsap-hero-title text-6xl md:text-8xl lg:text-9xl font-bold leading-none tracking-tight text-white">
						BUILDING <br />
						<span class="text-primary">CAPACITY.</span>
					</div>
					<div class="gsap-hero-title text-5xl md:text-7xl lg:text-8xl font-bold leading-none tracking-tight text-white/40 text-glow-background">
						POWERING PROGRESS.
					</div>
				</h1>

				<p class="gsap-hero-sub text-lg md:text-2xl font-sans text-white/80 max-w-2xl font-light leading-relaxed">
					Caribbian International Ltd. executes turnkey commercial building projects,
					high-voltage industrial electrical grids, and multi-sector civil road
					infrastructure with zero safety compromise.
				</p>

				<!-- CTA Action Cluster -->
				<div class="gsap-hero-sub flex flex-wrap gap-5 pt-4">
					<a href="#rfq"
						class="bg-primary hover:bg-primary-dark text-white font-display text-lg uppercase tracking-wider px-8 py-5 transition-all duration-300 flex items-center gap-3 shadow-lg shadow-primary/20">
						Submit Project Tender <ArrowUpRight class="w-5 h-5" />
					</a>
					<a href="#services"
						class="border border-white/30 hover:border-white text-white font-display text-lg uppercase tracking-wider px-8 py-5 hover:bg-white hover:text-foreground transition-all duration-300">
						Explore Capabilities
					</a>
				</div>
			</div>

			<!-- Hero Visual Card: Multi-Disciplinary Site Team Image -->
			<div class="lg:col-span-4 relative">
				<div
					class="relative border-2 border-white/20 p-3 bg-foreground/80 backdrop-blur-md shadow-2xl">
					<!-- Image Tag Overlay -->
					<div
						class="absolute top-6 left-6 z-20 bg-foreground/90 px-3 py-1.5 border border-white/20 text-xs text-primary uppercase">
						On-Site Operations Team
					</div>

					<!-- Team Image Container -->
					<div class="aspect-[4/3] overflow-hidden relative">
						<img
							src="sitepose.jpeg"
							alt="Caribbian International On-Site Structural Engineering Team"
							class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700 scale-105 hover:scale-100" />
					</div>

					<div
						class="p-4 bg-white/5 border-t border-white/10 mt-3 text-xs text-white/70 space-y-1">
						<div class="flex justify-between">
							<span>PROJECT LEADERSHIP:</span>
							<span class="text-white font-bold">100% On-Site PPE Compliant</span>
						</div>
						<div class="flex justify-between">
							<span>SAFETY RATING:</span>
							<span class="text-primary font-bold">Zero Lost-Time Incidents</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- =================================================================== -->
<!-- HARD-NUMBERS PROOF STRIP (Turner / Kiewit Trust Bar) -->
<!-- =================================================================== -->
<section id="stats-bar" class="bg-background border-b border-grid py-12">
	<div class="container mx-auto px-6">
		<div
			class="grid grid-cols-2 md:grid-cols-4 divide-y md:divide-y-0 md:divide-x divide-grid border border-grid bg-white shadow-sm">
			<!-- Metric 1 -->
			<div
				class="gsap-stat-card p-8 md:p-10 group hover:bg-foreground hover:text-background transition-colors duration-500">
				<div class="flex items-center justify-between mb-4">
					<span
						class="font-mono text-xs uppercase tracking-widest text-foreground/50 group-hover:text-primary"
						>Operational History</span>
					<Calendar class="w-5 h-5 text-primary" />
				</div>
				<p class="font-mono text-4xl lg:text-6xl font-bold tracking-tight mb-1">
					12<span class="text-primary">+</span>
				</p>
				<p class="font-sans text-sm text-foreground/70 group-hover:text-white/70">
					Years of Continuous Engineering Execution
				</p>
			</div>

			<!-- Metric 2 -->
			<div
				class="gsap-stat-card p-8 md:p-10 group hover:bg-foreground hover:text-background transition-colors duration-500">
				<div class="flex items-center justify-between mb-4">
					<span
						class="font-mono text-xs uppercase tracking-widest text-foreground/50 group-hover:text-primary"
						>Projects Completed</span>
					<Briefcase class="w-5 h-5 text-primary" />
				</div>
				<p class="font-mono text-4xl lg:text-6xl font-bold tracking-tight mb-1">
					85<span class="text-primary">+</span>
				</p>
				<p class="font-sans text-sm text-foreground/70 group-hover:text-white/70">
					Commercial, Civil & Electrical Projects
				</p>
			</div>

			<!-- Metric 3 -->
			<div
				class="gsap-stat-card p-8 md:p-10 group hover:bg-foreground hover:text-background transition-colors duration-500">
				<div class="flex items-center justify-between mb-4">
					<span
						class="font-mono text-xs uppercase tracking-widest text-foreground/50 group-hover:text-primary"
						>Power Infrastructure</span>
					<Zap class="w-5 h-5 text-primary" />
				</div>
				<p class="font-mono text-4xl lg:text-6xl font-bold tracking-tight mb-1">
					45<span class="text-primary">MW</span>
				</p>
				<p class="font-sans text-sm text-foreground/70 group-hover:text-white/70">
					Transformer & Generator Capacity Commissioned
				</p>
			</div>

			<!-- Metric 4 -->
			<div class="gsap-stat-card p-8 md:p-10 bg-foreground text-background">
				<div class="flex items-center justify-between mb-4">
					<span class="font-mono text-xs uppercase tracking-widest text-white/50"
						>Site Safety Record</span>
					<ShieldCheck class="w-5 h-5 text-primary" />
				</div>
				<p
					class="font-mono text-4xl lg:text-6xl font-bold tracking-tight mb-1 text-primary">
					0.0
				</p>
				<p class="font-sans text-sm text-white/70">
					Lost-Time Incidents (LTI) Standard Maintained
				</p>
			</div>
		</div>
	</div>
</section>

<!-- =================================================================== -->
<!-- CORE DISCIPLINES & SERVICES (Organized strictly around 3 Pillars) -->
<!-- =================================================================== -->
<section id="services" class="py-32 bg-background border-b border-grid relative">
	<div class="container mx-auto px-6">
		<!-- Section Header -->
		<div class="flex flex-col lg:flex-row lg:items-end justify-between mb-20 gap-8">
			<div>
				<span class="font-mono text-xs uppercase text-primary mb-3 block">Engineering & Contracting Capabilities</span>
				<h2 class="text-5xl md:text-7xl font-bold text-foreground">CORE SERVICES</h2>
			</div>
			<p class="text-sm text-foreground/60 max-w-lg leading-relaxed border-l-2 border-primary pl-4">
				Our multi-disciplinary team eliminates operational friction by integrating civil
				foundation, structural erection, and high-capacity electrical setups into one
				unified delivery workflow.
			</p>
		</div>

		<!-- 3 Core Service Pillars Cards Grid -->
		<div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
			<!-- PILLAR 1: Industrial Electrical Work -->
            <div class="gsap-service-card">
                <div class="bg-white border border-grid p-10 flex flex-col justify-between hover:border-primary transition-all duration-300 shadow-sm group">
                    <div>
                        <div
                            class="w-16 h-16 bg-foreground text-primary flex items-center justify-center mb-8 group-hover:bg-primary group-hover:text-white transition-colors duration-300">
                            <Zap class="w-8 h-8" />
                        </div>
    
                        <h3 class="text-3xl font-bold mb-4 group-hover:text-primary transition-colors">
                            Industrial Electrical Systems
                        </h3>
    
                        <p class="font-sans text-foreground/70 leading-relaxed mb-8">
                            Complete high-voltage power distribution setups, commercial switchgear
                            integration, step-down transformer installations, and synchronized backup
                            generator power plants for manufacturing and industrial facilities.
                        </p>
    
                        <div
                            class="space-y-3 text-sm border-t border-grid pt-6 mb-8 text-foreground/80">
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Heavy Duty Transformer Installation</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Automatic Switchgear & Panelboards</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Commercial Generator Synchronization</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>High-Voltage Power Grid Distribution</span>
                            </div>
                        </div>
                    </div>
    
                    <a
                        href="#rfq"
                        class="inline-flex items-center gap-2 font-display text-sm uppercase tracking-wider text-foreground group-hover:text-primary transition-colors">
                        Request Electrical Scope <ChevronRight class="w-4 h-4" />
                    </a>
                </div>
            </div>

			<!-- PILLAR 2: Commercial Construction -->
            <div class="gsap-service-card">
                <div class="bg-white border border-grid p-10 flex flex-col justify-between hover:border-primary transition-all duration-300 shadow-sm group">
                    <div>
                        <div
                            class="w-16 h-16 bg-foreground text-primary flex items-center justify-center mb-8 group-hover:bg-primary group-hover:text-white transition-colors duration-300">
                            <Building2 class="w-8 h-8" />
                        </div>
    
                        <h3 class="text-3xl font-bold mb-4 group-hover:text-primary transition-colors">
                            Commercial Construction
                        </h3>
    
                        <p class="font-sans text-foreground/70 leading-relaxed mb-8">
                            Turnkey commercial building development, multi-story structural concrete
                            framing, steel warehouse erection, retrofits, and full-scale architectural
                            general contracting for corporate and public sector clients.
                        </p>
    
                        <div
                            class="space-y-3 text-sm border-t border-grid pt-6 mb-8 text-foreground/80">
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Structural Concrete & Foundation Framing</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Heavy Steel Structure Erection</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Industrial Warehouses & Business Parks</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>General Contracting & Site Oversight</span>
                            </div>
                        </div>
                    </div>
    
                    <a
                        href="#rfq"
                        class="inline-flex items-center gap-2 font-display text-sm uppercase tracking-wider text-foreground group-hover:text-primary transition-colors">
                        Request Construction Scope <ChevronRight class="w-4 h-4" />
                    </a>
                </div>
            </div>

			<!-- PILLAR 3: Civil Engineering & Road Construction -->
            <div class="gsap-service-card">
                <div class="bg-white border border-grid p-10 flex flex-col justify-between hover:border-primary transition-all duration-300 shadow-sm group">
                    <div>
                        <div
                            class="w-16 h-16 bg-foreground text-primary flex items-center justify-center mb-8 group-hover:bg-primary group-hover:text-white transition-colors duration-300">
                            <Truck class="w-8 h-8" />
                        </div>
    
                        <h3 class="text-3xl font-bold mb-4 group-hover:text-primary transition-colors">
                            Civil Engineering & Roads
                        </h3>
    
                        <p class="font-sans text-foreground/70 leading-relaxed mb-8">
                            Major civil infrastructure development, road network paving, earthworks,
                            site leveling, storm water drainage engineering, and reinforced concrete
                            bridge structures built for heavy transit loads.
                        </p>
    
                        <div
                            class="space-y-3 text-sm border-t border-grid pt-6 mb-8 text-foreground/80">
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Asphalt & Concrete Highway Paving</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Earthworks, Excavation & Site Grading</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Municipal Drainage & Retaining Structures</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <CircleCheck class="w-4 h-4 text-primary shrink-0" />
                                <span>Bridge Deck & Heavy Transit Infrastructure</span>
                            </div>
                        </div>
                    </div>
    
                    <a
                        href="#rfq"
                        class="inline-flex items-center gap-2 font-display text-sm uppercase tracking-wider text-foreground group-hover:text-primary transition-colors">
                        Request Civil Scope <ChevronRight class="w-4 h-4" />
                    </a>
                </div>
            </div>
		</div>
	</div>
</section>

<!-- =================================================================== -->
<!-- FEATURED PROJECT PORTFOLIO SHOWCASE (Suffolk / PCL Filtered Grid) -->
<!-- =================================================================== -->
<section id="projects" class="py-32 bg-foreground text-background">
	<div class="container mx-auto px-6">
		<div class="flex flex-col lg:flex-row lg:items-end justify-between mb-16 gap-8">
			<div>
				<span class="font-mono text-xs uppercase tracking-widest text-primary mb-3 block"
					>Track Record & Field Operations</span>
				<h2 class="text-5xl md:text-7xl font-bold text-white">PROJECT PORTFOLIO</h2>
			</div>

			<!-- Filter Controls -->
			<div class="flex flex-wrap gap-2 text-xs uppercase">
				<button
					onclick={() => (activeTab = "all")}
					class="px-5 py-3 border transition-colors {activeTab === 'all'
						? 'bg-primary border-primary text-white'
						: 'border-white/20 text-white/70 hover:border-white'}">
					All Scope
				</button>
				<button
					onclick={() => (activeTab = "electrical")}
					class="px-5 py-3 border transition-colors {activeTab === 'electrical'
						? 'bg-primary border-primary text-white'
						: 'border-white/20 text-white/70 hover:border-white'}">
					Electrical
				</button>
				<button
					onclick={() => (activeTab = "construction")}
					class="px-5 py-3 border transition-colors {activeTab === 'construction'
						? 'bg-primary border-primary text-white'
						: 'border-white/20 text-white/70 hover:border-white'}">
					Construction
				</button>
				<button
					onclick={() => (activeTab = "civil")}
					class="px-5 py-3 border transition-colors {activeTab === 'civil'
						? 'bg-primary border-primary text-white'
						: 'border-white/20 text-white/70 hover:border-white'}">
					Civil & Roads
				</button>
			</div>
		</div>

		<!-- Projects Grid -->
		<div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
			{#each filteredProjects as project (project.id)}
                <div class="gsap-project-card">
                    <div class="bg-white/5 border border-white/10 overflow-hidden flex flex-col justify-between hover:border-primary transition-all duration-300 group">
                        <div>
                            <!-- Media Aspect Container -->
                            <div class="aspect-[16/10] relative overflow-hidden bg-foreground/50">
                                <img
                                    src={project.image}
                                    alt={project.title}
                                    class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" />
                                <div
                                    class="absolute top-4 left-4 bg-foreground/90 text-primary text-xs px-3 py-1 border border-white/10 uppercase">
                                    {project.categoryLabel}
                                </div>
                            </div>
    
                            <div class="p-8">
                                <div
                                    class="flex justify-between items-center text-white/40 text-xs mb-3">
                                    <span>{project.location}</span>
                                    <span>COMPLETED {project.year}</span>
                                </div>
    
                                <h3
                                    class="text-2xl font-bold text-white mb-4 group-hover:text-primary transition-colors">
                                    {project.title}
                                </h3>
    
                                <p class="font-sans text-white/70 text-sm leading-relaxed mb-6">
                                    {project.description}
                                </p>
                            </div>
                        </div>
    
                        <!-- Technical Metrics Bar (JetBrains Mono) -->
                        <div
                            class="p-6 bg-black/40 border-t border-white/10 grid grid-cols-3 gap-2 text-xs text-white/60">
                            <div>
                                <span class="block text-white/30 uppercase text-[10px]">Spec</span>
                                <span class="text-white font-bold">{project.metrics.primary}</span>
                            </div>
                            <div>
                                <span class="block text-white/30 uppercase text-[10px]">Detail</span>
                                <span class="text-white">{project.metrics.secondary}</span>
                            </div>
                            <div>
                                <span class="block text-white/30 uppercase text-[10px]">Scale</span>
                                <span class="text-primary font-bold">{project.metrics.scale}</span>
                            </div>
                        </div>
                    </div>
                </div>
			{/each}
		</div>
	</div>
</section>

<!-- =================================================================== -->
<!-- SAFETY, HSE & OPERATIONAL EXCELLENCE (McCarthy / Turner Safety Culture) -->
<!-- =================================================================== -->
<section id="safety" class="py-32 bg-background border-b border-grid">
	<div class="container mx-auto px-6">
		<div class="grid grid-cols-1 lg:grid-cols-12 gap-16 items-center">
			<!-- Left Visual: Civil Engineers on Site in Full PPE -->
			<div class="lg:col-span-5 relative">
				<div class="border-2 border-foreground p-3 bg-white shadow-xl relative z-10">
					<div class="aspect-[4/3] overflow-hidden">
						<img
							src="sitepose.jpeg"
							alt="Caribbian International Engineers Conduct Site Safety Inspection"
							class="w-full h-full object-cover" />
					</div>
					<div
						class="p-4 bg-foreground text-background text-xs mt-3 flex justify-between items-center">
						<span>FIELD OPERATIONS VERIFICATION</span>
						<span class="text-primary font-bold">100% SITE AUDITED</span>
					</div>
				</div>

				<!-- Decorative Blueprint Element -->
				<div
					class="absolute -bottom-8 -right-8 w-full h-full border-2 border-dashed border-primary/40 -z-0 hidden md:block">
				</div>
			</div>

			<!-- Right Content Block -->
			<div class="lg:col-span-7 space-y-8 gsap-safety-content">
				<div
					class="inline-flex items-center gap-2 bg-primary/10 text-primary px-3 py-1 text-xs uppercase tracking-wider">
					<ShieldCheck class="w-4 h-4" /> Zero-Harm Safety Protocol
				</div>

				<h2 class="text-5xl md:text-7xl font-bold">
					HIRE US TODAY FOR A <br />
					<span class="text-primary">SAFER TOMORROW.</span>
				</h2>

				<p class="font-sans text-xl text-foreground/80 leading-relaxed">
					In high-stakes commercial construction and high-voltage electrical
					installations, safety isn't an afterthought—it's the primary qualification gate.
				</p>

				<div class="grid grid-cols-1 md:grid-cols-2 gap-6 pt-4">
					<div class="border-l-4 border-primary pl-4 space-y-2">
						<h4 class="font-display text-xl">Daily Toolbox Briefings</h4>
						<p class="font-sans text-sm text-foreground/70">
							Mandatory daily hazard assessments conducted prior to site machinery
							activation.
						</p>
					</div>
					<div class="border-l-4 border-primary pl-4 space-y-2">
						<h4 class="font-display text-xl">ISO & Local Regulatory Compliance</h4>
						<p class="font-sans text-sm text-foreground/70">
							Full adherence to national building codes, environmental standards, and
							electrical safety bylaws.
						</p>
					</div>
				</div>

				<!-- Partner/Registry Badges -->
				<div class="pt-6 border-t border-grid">
					<p class="font-mono text-xs uppercase text-foreground/50 mb-4">
						Certified & Registered Contracting Partner:
					</p>
					<div class="flex flex-wrap gap-4 opacity-80">
						<div
							class="px-4 py-2 border border-grid text-xs uppercase bg-white">
							National Engineers Board
						</div>
						<div
							class="px-4 py-2 border border-grid text-xs uppercase bg-white">
							Public Procurement Registry
						</div>
						<div
							class="px-4 py-2 border border-grid text-xs uppercase bg-white">
							ISO 9001:2015 Standards
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- =================================================================== -->
<!-- SUBCONTRACTORS & PARTNER PORTAL (Kiewit Subcontractor Callout) -->
<!-- =================================================================== -->
<section id="subcontractors" class="py-24 bg-foreground/5 border-b border-grid">
	<div class="container mx-auto px-6">
		<div
			class="bg-white border border-grid p-12 md:p-16 flex flex-col lg:flex-row items-center justify-between gap-12 shadow-sm">
			<div class="space-y-4 max-w-2xl">
				<span class="font-mono text-xs uppercase tracking-widest text-primary"
					>Partner Ecosystem</span>
				<h3 class="text-4xl md:text-5xl font-bold">SUBCONTRACTORS & MATERIAL SUPPLIERS</h3>
				<p class="font-sans text-foreground/70 leading-relaxed">
					We partner with specialized trades, equipment operators, and certified material
					vendors across our civil, structural, and high-voltage electrical projects.
					Register your firm to be included in our preferred bidding pool.
				</p>
			</div>

			<div class="shrink-0 flex flex-col sm:flex-row gap-4 w-full lg:w-auto">
				<a
					href="#rfq"
					class="border border-foreground hover:bg-foreground hover:text-white px-8 py-5 font-display text-sm uppercase tracking-wider text-center transition-colors">
					Vendor Registration
				</a>
				<a
					href="/company-profile.pdf"
					download
					class="bg-primary hover:bg-primary-dark text-white px-8 py-5 font-display text-sm uppercase tracking-wider text-center transition-colors flex items-center justify-center gap-2">
					<Download class="w-4 h-4" /> Download Prequalification PDF
				</a>
			</div>
		</div>
	</div>
</section>

<!-- =================================================================== -->
<!-- RFQ / TENDER SUBMISSION DESK (Bidding & Contracting Portal) -->
<!-- =================================================================== -->
<section id="rfq" class="py-32 bg-background relative">
	<div class="container mx-auto px-6 max-w-5xl">
		<div class="text-center space-y-4 mb-16">
			<span class="font-mono text-xs uppercase tracking-widest text-primary"
				>Direct Contracting Desk</span>
			<h2 class="text-5xl md:text-7xl font-bold">REQUEST A PROPOSAL / TENDER SUBMISSION</h2>
			<p class="font-sans text-foreground/70 text-lg max-w-2xl mx-auto">
				Submit your project scope, Bill of Quantities (BOQ), or RFQ documentation directly
				to our engineering bid estimation team.
			</p>
		</div>

		<!-- RFQ Form Box -->
		<div class="bg-white border border-grid p-8 md:p-16 shadow-xl relative">
			<form
				class="space-y-8"
				onsubmit={(e) => {
                    e.preventDefault()
					alert(
						"Tender document submitted. Our estimation engineering desk will contact you within 24 hours.",
					)}}>
				<div class="grid grid-cols-1 md:grid-cols-2 gap-8">
					<div class="space-y-2">
						<label
							for="organization"
							class="block text-xs uppercase text-foreground/70"
							>Organization / Client Name *</label>
						<input
							type="text"
							id="organization"
							required
							class="w-full border-b border-grid bg-transparent py-3 font-sans focus:outline-none focus:border-primary transition-colors text-foreground"
							placeholder="e.g. Ministry of Works / Commercial Dev Corp" />
					</div>

					<div class="space-y-2">
						<label
							for="contact-email"
							class="block text-xs uppercase text-foreground/70"
							>Official Email Address *</label>
						<input
							type="email"
							id="contact-email"
							required
							class="w-full border-b border-grid bg-transparent py-3 font-sans focus:outline-none focus:border-primary transition-colors text-foreground"
							placeholder="procurement@organization.com" />
					</div>
				</div>

				<div class="grid grid-cols-1 md:grid-cols-2 gap-8">
					<div class="space-y-2">
						<label
							for="tender-ref"
							class="block text-xs uppercase text-foreground/70"
							>Tender Ref / Project ID (Optional)</label>
						<input
							type="text"
							id="tender-ref"
							class="w-full border-b border-grid bg-transparent py-3 font-sans focus:outline-none focus:border-primary transition-colors text-foreground"
							placeholder="e.g. TND-2026-88B" />
					</div>

					<div class="space-y-2">
						<label
							for="primary-scope"
							class="block text-xs uppercase text-foreground/70"
							>Primary Service Discipline *</label>
						<select
							id="primary-scope"
							required
							class="w-full border-b border-grid bg-transparent py-3 font-sans focus:outline-none focus:border-primary transition-colors text-foreground rounded-none appearance-none">
							<option value="combined">Multi-Discipline (Full EPC Scope)</option>
							<option value="electrical"
								>Industrial Electrical (Transformers, Generators, Grid Setup)</option>
							<option value="construction">Commercial Construction & Framing</option>
							<option value="civil">Civil Engineering & Road Construction</option>
						</select>
					</div>
				</div>

				<div class="space-y-2">
					<label
						for="project-details"
						class="block text-xs uppercase text-foreground/70"
						>Project Summary / Scope Details</label>
					<textarea
						id="project-details"
						rows="4"
						class="w-full border-b border-grid bg-transparent py-3 font-sans focus:outline-none focus:border-primary transition-colors text-foreground"
						placeholder="Provide details regarding project location, estimated start date, required capacity (MW/m²), or structural requirements..."
					></textarea>
				</div>

				<!-- File Upload Dropzone -->
				<div class="space-y-2">
					<span class="block text-xs uppercase text-foreground/70"
						>Attach Scope / BOQ / Tender Drawings (PDF, XLSX)</span>
					<div
						class="border-2 border-dashed border-grid p-10 text-center hover:bg-foreground/5 hover:border-primary transition-all duration-300 cursor-pointer group">
						<Upload
							class="w-8 h-8 text-foreground/40 group-hover:text-primary mx-auto mb-3 transition-colors" />
						<p class="font-sans text-sm text-foreground/70 group-hover:text-foreground">
							Click to upload or drag tender specification files here
						</p>
						<p class="font-mono text-xs text-foreground/40 mt-1">
							Maximum file payload size: 50MB
						</p>
					</div>
				</div>

				<!-- Restrained Accent Button for Critical Conversion Path -->
				<button
					type="submit"
					class="w-full bg-accent hover:bg-accent/90 text-white font-display text-xl uppercase tracking-widest py-6 transition-colors shadow-lg shadow-accent/20 flex items-center justify-center gap-3">
					<Upload class="w-5 h-5" /> Submit Documentation To Engineering Desk
				</button>
			</form>
		</div>
	</div>
</section>
