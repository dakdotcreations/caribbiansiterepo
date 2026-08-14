<script>
	import { useGsap } from "$lib/utils/useGsap" // Adjust import path to your wrapper
	import { gsap } from "gsap"

	// Lucide Icons
	import {
		ShieldCheck,
		HardHat,
		ClipboardCheck,
		AlertOctagon,
		Activity,
		Leaf,
		ArrowRight,
	} from "@lucide/svelte"

	useGsap(() => {
		// Hero Typography Stagger
		gsap.from(".hero-text-line", {
			y: 100,
			opacity: 0,
			duration: 1.2,
			stagger: 0.15,
			ease: "power4.out",
			delay: 0.2,
		})

		gsap.from(".hero-meta", {
			opacity: 0,
			x: -20,
			duration: 1,
			delay: 0.8,
			ease: "power2.out",
		})

		// Scroll Reveal Elements
		const revealSections = gsap.utils.toArray(".scroll-reveal")
		revealSections.forEach((section) => {
			gsap.from(section, {
				scrollTrigger: {
					trigger: section,
					start: "top 85%",
					toggleActions: "play none none reverse",
				},
				y: 40,
				opacity: 0,
				duration: 1,
				ease: "power3.out",
			})
		})

		// Parallax Image scaling
		const projectImages = gsap.utils.toArray(".parallax-img img")
		projectImages.forEach((img) => {
			gsap.fromTo(
				img,
				{ scale: 1.15 },
				{
					scale: 1,
					scrollTrigger: {
						trigger: img.parentElement,
						start: "top bottom",
						end: "bottom top",
						scrub: true,
					},
				},
			)
		})
	})
</script>

<!-- HERO SECTION -->
<section
	class="relative pt-40 pb-32 border-b border-grid overflow-hidden bg-foreground text-background">
	<div class="absolute inset-0 z-0 opacity-20">
		<img
			src="/api/placeholder/1920/1080"
			alt="Site Safety Briefing"
			class="w-full h-full object-cover mix-blend-luminosity" />
		<div
			class="absolute inset-0 bg-linear-to-t from-foreground via-foreground/80 to-transparent">
		</div>
	</div>

	<div class="container mx-auto px-6 relative z-10">
		<div class="flex items-center gap-4 mb-8 overflow-hidden hero-meta">
			<ShieldCheck class="w-6 h-6 text-primary" />
			<p class="font-mono uppercase tracking-widest text-sm text-primary">
				Health, Safety & Environment (HSE)
			</p>
		</div>

		<div class="overflow-hidden mb-2">
			<h1 class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line">ZERO</h1>
		</div>
		<div class="overflow-hidden mb-2">
			<h1 class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line text-primary">
				COMPROMISE.
			</h1>
		</div>

		<div class="mt-12 overflow-hidden max-w-3xl hero-text-line">
			<p
				class="font-sans text-xl md:text-2xl text-background/80 leading-relaxed border-l-4 border-primary pl-6">
				Safety is not a department or a checklist. It is our operational baseline. Every
				shift, every site, and every structure is governed by an absolute commitment to
				returning our people home safely.
			</p>
		</div>
	</div>
</section>

<!-- THE COMMITMENT (Statement of Authority) -->
<section class="py-24 bg-background border-b border-grid">
	<div class="container mx-auto px-6">
		<div class="grid grid-cols-1 lg:grid-cols-12 gap-16 items-center">
			<div class="lg:col-span-5 scroll-reveal">
				<h2 class="text-4xl md:text-6xl mb-8">STOP WORK <br />AUTHORITY.</h2>
				<p class="font-sans text-lg text-foreground/70 mb-6 leading-relaxed">
					At Caribbian International Ltd., every single employee on a job site from the lead civil engineer to the newest sub-contractor—carries absolute <strong>Stop Work Authority</strong>.
				</p>
				<p class="font-sans text-lg text-foreground/70 leading-relaxed">
					If a hazard is identified during heavy electrical integration, structural steel
					erection, or heavy earthworks, work halts immediately. Production never
					supersedes safety.
				</p>
			</div>
			<div
				class="lg:col-span-7 parallax-img overflow-hidden h-125 bg-foreground w-full scroll-reveal">
				<img
					src="/safety.jpeg"
					alt="Engineers Inspecting Plans"
					class="w-full h-full object-cover opacity-90" />
			</div>
		</div>
	</div>
</section>

<!-- CORE SAFETY PILLARS -->
<section class="py-32 bg-white border-b border-grid">
	<div class="container mx-auto px-6">
		<div class="text-center mb-24 scroll-reveal">
			<p class="font-mono text-primary text-sm uppercase mb-4 tracking-widest">
				Operational Framework
			</p>
			<h2 class="text-5xl md:text-7xl mb-6">THE 4 PILLARS OF <br />SITE EXECUTION</h2>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-0 border border-grid bg-grid">
			<!-- Pillar 1 -->
			<div
				class="p-12 md:p-16 border-b md:border-r border-grid hover:bg-foreground hover:text-background transition-colors duration-500 group scroll-reveal">
				<ClipboardCheck
					class="w-12 h-12 text-primary mb-8 transform group-hover:scale-110 transition-transform duration-500" />
				<h3 class="text-3xl mb-4 group-hover:text-white">Job Hazard Analysis (JHA)</h3>
				<p
					class="font-sans text-foreground/70 group-hover:text-background/70 leading-relaxed">
					Before any high-voltage system is energized or ground is broken, site specific risk assessments map out potential hazards, establishing concrete mitigation protocols.
				</p>
			</div>

			<!-- Pillar 2 -->
			<div
				class="p-12 md:p-16 border-b border-grid hover:bg-foreground hover:text-background transition-colors duration-500 group scroll-reveal">
				<HardHat
					class="w-12 h-12 text-primary mb-8 transform group-hover:scale-110 transition-transform duration-500" />
				<h3 class="text-3xl mb-4 group-hover:text-white">Mandatory Toolbox Talks</h3>
				<p
					class="font-sans text-foreground/70 group-hover:text-background/70 leading-relaxed">
					Daily site briefings ensure all personnel are aligned on the day's specific structural or civil engineering tasks, heavy machinery movement, and environmental conditions.
				</p>
			</div>

			<!-- Pillar 3 -->
			<div
				class="p-12 md:p-16 border-b md:border-b-0 md:border-r border-grid hover:bg-foreground hover:text-background transition-colors duration-500 group scroll-reveal">
				<Activity
					class="w-12 h-12 text-primary mb-8 transform group-hover:scale-110 transition-transform duration-500" />
				<h3 class="text-3xl mb-4 group-hover:text-white">Continuous Training</h3>
				<p
					class="font-sans text-foreground/70 group-hover:text-background/70 leading-relaxed">
					Our electrical and civil crews undergo continuous OSHA and national engineering board aligned training to remain at the forefront of safe industrial operational standards.
				</p>
			</div>

			<!-- Pillar 4 -->
			<div
				class="p-12 md:p-16 hover:bg-foreground hover:text-background transition-colors duration-500 group scroll-reveal">
				<Leaf
					class="w-12 h-12 text-primary mb-8 transform group-hover:scale-110 transition-transform duration-500" />
				<h3 class="text-3xl mb-4 group-hover:text-white">Environmental Protection</h3>
				<p
					class="font-sans text-foreground/70 group-hover:text-background/70 leading-relaxed">
					From road construction run-off management to commercial waste disposal, we engineer our sites to minimize ecological footprint and protect local communities.
				</p>
			</div>
		</div>
	</div>
</section>

<!-- SAFETY METRICS (Forcing the client to provide scale) -->
<section class="py-24 bg-foreground text-background border-b-8 border-primary">
	<div class="container mx-auto px-6">
		<div
			class="flex flex-col md:flex-row md:items-end justify-between mb-16 gap-8 scroll-reveal">
			<div>
				<h2 class="text-4xl md:text-6xl text-white">SAFETY <br />BY THE NUMBERS</h2>
			</div>
			<p
				class="font-mono text-background/60 max-w-md text-sm uppercase leading-relaxed border-l-2 border-primary pl-4">
				Our track record secures our position as a preferred bidder for government and tier-1 corporate infrastructure tenders.
			</p>
		</div>

		<div
			class="grid grid-cols-1 md:grid-cols-3 divide-y md:divide-y-0 md:divide-x divide-white/10 border border-white/10 scroll-reveal">
			<div class="p-10 text-center">
				<p class="font-mono text-background/50 text-sm uppercase mb-4">
					Experience Modification Rate (EMR)
				</p>
				<p class="font-mono text-5xl md:text-7xl font-bold text-white mb-2">0.78</p>
				<p class="font-sans text-sm text-primary">Industry Leading Standard</p>
			</div>

			<div class="p-10 text-center">
				<p class="font-mono text-background/50 text-sm uppercase mb-4">
					Total Recordable Incident Rate (TRIR)
				</p>
				<p class="font-mono text-5xl md:text-7xl font-bold text-white mb-2">0.10</p>
				<p class="font-sans text-sm text-primary">Below National Average</p>
			</div>

			<div class="p-10 text-center bg-primary text-white">
				<p class="font-mono text-white/70 text-sm uppercase mb-4">
					Lost Time Incidents (YTD)
				</p>
				<p class="font-mono text-5xl md:text-7xl font-bold mb-2">0</p>
				<p class="font-sans text-sm text-white/90">Across All Active Sites</p>
			</div>
		</div>
	</div>
</section>

<!-- REPORTING & COMPLIANCE (Pre-footer CTA) -->
<section class="py-32 bg-background">
	<div class="container mx-auto px-6 text-center max-w-4xl scroll-reveal">
		<AlertOctagon class="w-16 h-16 text-foreground mx-auto mb-8 opacity-20" />
		<h2 class="text-4xl md:text-5xl mb-6">PROCUREMENT & COMPLIANCE</h2>
		<p class="font-sans text-xl text-foreground/70 mb-10 leading-relaxed">
			Full documentation of our Health, Safety, and Environment policies, including insurance certificates and detailed incident history, is available for tender review boards and procurement officers.
		</p>

		<div class="flex flex-col sm:flex-row justify-center gap-6">
			<a
				href="/contact"
				class="bg-foreground text-background font-display text-lg uppercase px-10 py-5 hover:bg-primary transition-colors flex items-center justify-center gap-2">
				Request HSE Documents <ArrowRight class="w-5 h-5" />
			</a>
		</div>
	</div>
</section>
