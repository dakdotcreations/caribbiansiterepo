<script>
	import { useGsap } from "$lib/utils/useGsap" // Adjust import path to your wrapper
	import { gsap } from "gsap"

	import {
		Building2,
		Zap,
		Layers,
		Compass,
		Check,
		Truck,
		ArrowUpRight,
		ShieldCheck,
		Wrench,
		CheckCircle2,
	} from "@lucide/svelte"

	const divisions = [
		{
			id: "01",
			title: "Civil & Structural Engineering",
			icon: Building2,
			subtitle:
				"Heavy foundation engineering, steel superstructures, and concrete civil works.",
			description:
				"Our civil division handles complex structural challenges for commercial towers, industrial facilities, bridges, and municipal infrastructure. We self-perform deep excavation, piling, post-tensioned concrete, and structural steel erection.",
			capabilities: [
				"Deep Foundation & Piling Operations",
				"Post-Tensioned & Reinforced Concrete",
				"Structural Steel Design & Erection",
				"Bridge & Overpass Construction",
				"Industrial Plant Retaining Structures",
			],
			img: "/civil.jpeg",
		},
		{
			id: "02",
			title: "High Voltage & Heavy Electrical",
			icon: Zap,
			subtitle:
				"Turnkey electrical grid integration, substations, and industrial power distribution.",
			description:
				"Equipped to handle high-voltage utility installations and complex industrial electrical distribution. From 400kV power substations to industrial SCADA systems, our certified electrical engineers deliver reliable, grid-compliant energy infrastructure.",
			capabilities: [
				"400kV Substation Construction & Commissioning",
				"High-Voltage Underground Trenching & Cabling",
				"Industrial Power Distribution & Switchgear",
				"SCADA & Automation System Integration",
				"Backup Generator & Microgrid Deployment",
			],
			img: "/electricity.jpeg",
		},
		{
			id: "03",
			title: "Bulk Earthworks & Site Engineering",
			icon: Layers,
			subtitle: "Mass excavation, precise GPS land grading, and utility infrastructure.",
			description:
				"Utilizing a company-owned heavy equipment fleet equipped with 3D GPS grading technology, we prepare massive acreage for highway construction, industrial parks, and energy sites with speed and millimeter accuracy.",
			capabilities: [
				"Mass Land Clearing & Rock Excavation",
				"GPS-Guided Precision Soil Grading",
				"Sub-surface Stormwater & Sewage Infrastructure",
				"Roadway Paving & Soil Stabilization",
				"Erosion Control & Environmental Mitigation",
			],
			img: "/earthworks.jpeg",
		},
		{
			id: "04",
			title: "EPC & Turnkey Project Management",
			icon: Compass,
			subtitle: "End-to-end Engineering, Procurement, and Construction management.",
			description:
				"For clients seeking a single point of accountability, our EPC division coordinates everything from initial feasibility studies and architectural engineering to global procurement, construction, and final QA/QC handover.",
			capabilities: [
				"Design-Build & EPC Contracting",
				"Global Equipment & Material Procurement",
				"Rigorous Quality Assurance / Quality Control (QA/QC)",
				"Building Information Modeling (BIM 5D)",
				"Regulatory & Permitting Compliance Management",
			],
			img: "/epc.jpeg",
		},
	]

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

		// Division cards reveal animation
		const divisionRows = gsap.utils.toArray(".division-block")
		divisionRows.forEach((row) => {
			gsap.from(row, {
				scrollTrigger: {
					trigger: row,
					start: "top 80%",
				},
				y: 60,
				opacity: 0,
				duration: 1.2,
				ease: "power3.out",
			})
		})

		// Parallax effect on fleet section
		gsap.from(".fleet-banner", {
			scrollTrigger: {
				trigger: ".fleet-section",
				start: "top bottom",
				end: "bottom top",
				scrub: true,
			},
			y: -50,
		})
	})
</script>

<!-- HERO SECTION -->
<section class="relative pt-40 pb-32 bg-background border-b border-grid overflow-hidden">
	<div class="container mx-auto px-6">
		<div class="overflow-hidden mb-2">
			<h1 class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line">CORE</h1>
		</div>
		<div class="overflow-hidden mb-2">
			<h1 class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line text-primary">
				DIVISIONS.
			</h1>
		</div>
		<div class="overflow-hidden mb-12">
			<h1
				class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line text-foreground/40">
				SELF-PERFORMED.
			</h1>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-12 gap-8 items-end">
			<div class="md:col-span-8 overflow-hidden">
				<p
					class="font-sans text-xl md:text-2xl text-foreground/80 leading-relaxed border-l-4 border-primary pl-6 hero-text-line">
					We maintain total operational self-performance across civil, structural,
					electrical, and earthmoving sectors. Minimizing reliance on sub-contractors
					gives us complete command over project schedule, budget, and site safety.
				</p>
			</div>
			<div class="md:col-span-4 flex justify-start md:justify-end hero-text-line">
				<div class="p-6 bg-white border border-grid text-left">
					<p class="font-mono text-xs uppercase tracking-widest text-primary mb-1">
						Direct Fleet & Labor
					</p>
					<p class="font-mono text-3xl font-bold">85%+ SELF-PERFORMED</p>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- DIVISIONS LIST -->
<section class="py-24 bg-white border-b border-grid">
	<div class="container mx-auto px-6">
		<div class="space-y-32">
			{#each divisions as div, i}
				<div
					class="division-block border border-grid bg-background p-8 md:p-16 relative overflow-hidden">
					<!-- Large Decorative Number background -->
					<span
						class="absolute top-4 right-8 font-mono text-8xl md:text-9xl font-black text-foreground/5 pointer-events-none select-none">
						{div.id}
					</span>

					<div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center relative z-10">
						<!-- Content Left -->
						<div class="lg:col-span-7">
							<div class="flex items-center gap-3 mb-6">
								<svelte:component this={div.icon} class="w-8 h-8 text-primary" />
								<p class="font-mono text-primary text-sm uppercase tracking-widest">
									Division {div.id}
								</p>
							</div>

							<h2 class="text-4xl md:text-5xl font-display mb-4">{div.title}</h2>
							<p class="font-mono text-lg text-foreground/60 mb-6">{div.subtitle}</p>

							<p class="font-sans text-foreground/80 leading-relaxed mb-8">
								{div.description}
							</p>

							<!-- Capabilities list -->
							<div class="mb-8">
								<p
									class="font-mono text-xs uppercase tracking-wider text-foreground/50 mb-4">
									Core Capabilities Include:
								</p>
								<div class="grid grid-cols-1 md:grid-cols-2 gap-3">
									{#each div.capabilities as cap}
										<div class="flex items-start gap-2">
											<CheckCircle2
												class="w-5 h-5 text-primary shrink-0 mt-0.5" />
											<span class="font-sans text-sm text-foreground/90"
												>{cap}</span>
										</div>
									{/each}
								</div>
							</div>

							<a
								href="/contact"
								class="inline-flex items-center gap-2 font-display uppercase text-sm border-b-2 border-primary pb-1 hover:text-primary transition-colors">
								<span>Request Division Specs</span>
								<ArrowUpRight class="w-4 h-4" />
							</a>
						</div>

						<!-- Image Right -->
						<div
							class="lg:col-span-5 h-[350px] md:h-[450px] bg-foreground overflow-hidden border border-grid relative">
							<img
								src={div.img}
								alt={div.title}
								class="w-full h-full object-cover grayscale-[20%] hover:grayscale-0 transition-all duration-700 hover:scale-105" />
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- FLEET & EQUIPMENT CAPABILITY (Proves scale to procurement) -->
<section class="fleet-section py-28 bg-foreground text-background overflow-hidden relative">
	<div class="container mx-auto px-6 relative z-10">
		<div class="grid grid-cols-1 lg:grid-cols-12 gap-16 items-center">
			<div class="lg:col-span-5">
				<div
					class="flex items-center gap-2 text-primary font-mono text-sm uppercase tracking-widest mb-4">
					<Truck class="w-5 h-5" />
					<span>Capital Fleet Equipment</span>
				</div>
				<h2 class="text-4xl md:text-6xl text-white mb-6">OWNED MACHINERY & ASSETS</h2>
				<p class="font-sans text-background/70 text-lg leading-relaxed mb-8">
					We do not suffer from third-party equipment availability delays. Our
					multi-million dollar fleet of heavy excavators, mobile concrete batch plants,
					high-tonnage cranes, and GPS graders are owned, maintained, and ready for rapid
					mobilization.
				</p>

				<div class="grid grid-cols-2 gap-6 border-t border-white/10 pt-8 font-mono">
					<div>
						<p class="text-3xl text-primary font-bold">120+</p>
						<p class="text-xs uppercase text-background/60 mt-1">Heavy Machines</p>
					</div>
					<div>
						<p class="text-3xl text-primary font-bold">100%</p>
						<p class="text-xs uppercase text-background/60 mt-1">GPS-Integrated</p>
					</div>
					<div>
						<p class="text-3xl text-primary font-bold">24/7</p>
						<p class="text-xs uppercase text-background/60 mt-1">
							On-Site Fleet Maintenance
						</p>
					</div>
					<div>
						<p class="text-3xl text-primary font-bold">Zero</p>
						<p class="text-xs uppercase text-background/60 mt-1">Rental Dependencies</p>
					</div>
				</div>
			</div>

			<div class="lg:col-span-7 grid grid-cols-1 md:grid-cols-2 gap-6">
				<div class="p-8 bg-white/5 border border-white/10">
					<Wrench class="w-10 h-10 text-primary mb-4" />
					<h3 class="text-xl text-white font-mono mb-2">
						Heavy Excavation & Earthmoving
					</h3>
					<p class="font-sans text-sm text-background/60">
						High-capacity Caterpillar & Komatsu excavators, dozers, and articulated dump
						trucks for rapid site clearing.
					</p>
				</div>

				<div class="p-8 bg-white/5 border border-white/10">
					<Building2 class="w-10 h-10 text-primary mb-4" />
					<h3 class="text-xl text-white font-mono mb-2">Mobile Concrete Batching</h3>
					<p class="font-sans text-sm text-background/60">
						On-site continuous batching plants capable of delivering structural grade
						concrete directly to remote sites.
					</p>
				</div>

				<div class="p-8 bg-white/5 border border-white/10">
					<Zap class="w-10 h-10 text-primary mb-4" />
					<h3 class="text-xl text-white font-mono mb-2">High Voltage Testing Fleet</h3>
					<p class="font-sans text-sm text-background/60">
						Specialized mobile diagnostic labs for transformer testing, relay
						calibration, and underground fault detection.
					</p>
				</div>

				<div class="p-8 bg-white/5 border border-white/10">
					<ShieldCheck class="w-10 h-10 text-primary mb-4" />
					<h3 class="text-xl text-white font-mono mb-2">High-Tonnage Crane Lifting</h3>
					<p class="font-sans text-sm text-background/60">
						All-terrain mobile cranes for heavy structural steel placement, precast
						concrete, and transformer positioning.
					</p>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- BOTTOM CTA -->
<section class="py-24 bg-background border-t border-grid">
	<div class="container mx-auto px-6 text-center max-w-4xl">
		<h2 class="text-4xl md:text-5xl mb-6">NEED COMBINED DIVISION SERVICES?</h2>
		<p class="font-sans text-xl text-foreground/70 mb-10 leading-relaxed">
			Most of our major contracts combine earthmoving, civil engineering, and electrical
			integration under a unified EPC contract. Contact our technical team to discuss joint
			scope delivery.
		</p>

		<div class="flex flex-col sm:flex-row justify-center gap-6">
			<a
				href="/contact"
				class="bg-foreground text-background font-display text-lg uppercase px-10 py-5 hover:bg-primary transition-colors flex items-center justify-center gap-2">
				Inquire For Bid / RFP <ArrowUpRight class="w-5 h-5" />
			</a>
		</div>
	</div>
</section>
