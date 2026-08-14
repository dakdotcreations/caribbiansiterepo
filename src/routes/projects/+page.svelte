<script>
	import { useGsap } from "$lib/utils/useGsap" // Adjust import path to your wrapper
	import { gsap } from "gsap"

	import { ArrowUpRight, MapPin, Calendar, HardHat, CircleDollarSign } from "@lucide/svelte"

	// Mock data - Replace with your actual CMS data
	const projects = [
		{
			id: "01",
			title: "National Grid Substation Alpha",
			category: "High Voltage & Electrical",
			location: "Industrial District, Sector 4",
			duration: "18 Months",
			value: "$45M+",
			description:
				"Full turnkey construction of a 400kV substation. Scope included bulk earthworks, structural steel erection, heavy transformer integration, and rigorous QA/QC commissioning. Delivered with zero lost-time incidents.",
			img: "/api/placeholder/1600/900",
		},
		{
			id: "02",
			title: "Route 90 Highway Expansion",
			category: "Civil & Earthworks",
			location: "Northern Corridor",
			duration: "24 Months",
			value: "$120M+",
			description:
				"Mass excavation, grading, and paving of a 15-mile dual carriageway. Required complex logistical routing of heavy machinery and live-traffic management. Completed 2 months ahead of schedule.",
			img: "/api/placeholder/1600/900",
		},
		{
			id: "03",
			title: "Metro Commercial Hub Core",
			category: "Structural Concrete & Steel",
			location: "Downtown Financial District",
			duration: "14 Months",
			value: "$85M+",
			description:
				"Deep foundation pouring and steel superstructure erection for a 40-story commercial tower in a highly dense urban environment. Required precision crane logistics and nighttime concrete logistics.",
			img: "/api/placeholder/1600/900",
		},
	]

	useGsap(() => {
		// Hero Typography Stagger
		gsap.from(".hero-text-line", {
			y: 120,
			opacity: 0,
			duration: 1.2,
			stagger: 0.15,
			ease: "power4.out",
			delay: 0.2,
		})

		// Project Reveal Animations
		const projectRows = gsap.utils.toArray(".project-row")

		projectRows.forEach((row) => {
			const img = row.querySelector(".project-img")
			const mask = row.querySelector(".img-mask")
			const content = row.querySelector(".project-content")

			// The heavy image reveal mask
			gsap.to(mask, {
				scrollTrigger: {
					trigger: row,
					start: "top 75%",
				},
				height: 0,
				duration: 1.5,
				ease: "expo.inOut",
			})

			// Slight scale down on the image as the mask reveals it
			gsap.from(img, {
				scrollTrigger: {
					trigger: row,
					start: "top 75%",
				},
				scale: 1.2,
				duration: 2,
				ease: "power3.out",
			})

			// Fade up the text content
			gsap.from(content, {
				scrollTrigger: {
					trigger: row,
					start: "top 70%",
				},
				y: 50,
				opacity: 0,
				duration: 1,
				ease: "power3.out",
				delay: 0.4,
			})
		})
	})
</script>

<!-- HERO SECTION -->
<section class="relative pt-40 pb-32 bg-background border-b border-grid overflow-hidden">
	<div class="container mx-auto px-6">
		<div class="overflow-hidden mb-2">
			<h1 class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line">
				PROVEN SCALE.
			</h1>
		</div>
		<div class="overflow-hidden mb-2">
			<h1
				class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line text-foreground/40">
				FLAWLESS
			</h1>
		</div>
		<div class="overflow-hidden mb-12">
			<h1 class="text-6xl md:text-8xl lg:text-9xl leading-[0.9] hero-text-line text-primary">
				EXECUTION.
			</h1>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-12">
			<div class="overflow-hidden">
				<p
					class="font-sans text-xl md:text-2xl text-foreground/80 leading-relaxed border-l-4 border-primary pl-6 hero-text-line">
					Our portfolio is our proof. We do not just bid on complex infrastructure; we
					engineer it, manage it, and build it from the ground up.
				</p>
			</div>
			<div
				class="flex flex-wrap gap-4 items-end justify-start md:justify-end overflow-hidden">
				<div class="hero-text-line">
					<p class="font-mono text-xs uppercase tracking-widest text-foreground/50 mb-2">
						Sectors
					</p>
					<div class="flex gap-2">
						<span class="px-4 py-2 border border-grid text-sm font-mono bg-white"
							>CIVIL</span>
						<span class="px-4 py-2 border border-grid text-sm font-mono bg-white"
							>ELECTRICAL</span>
						<span class="px-4 py-2 border border-grid text-sm font-mono bg-white"
							>STRUCTURAL</span>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- PROJECTS LIST -->
<section class="bg-grid bg-white">
	{#each projects as project, i}
		<article
			class="project-row border-b border-grid py-24 md:py-32 relative overflow-hidden group">
			<div class="container mx-auto px-6">
				<div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-20 items-center">
					<!-- IMAGE COLUMN -->
					<!-- Alternate image position based on odd/even index -->
					<div
						class="lg:col-span-7 relative h-[400px] md:h-[600px] w-full {i % 2 !== 0
							? 'lg:order-last'
							: ''}">
						<!-- Mask for the reveal animation -->
						<div class="img-mask absolute inset-0 bg-foreground z-10 origin-bottom">
						</div>
						<div class="w-full h-full overflow-hidden relative border border-grid">
							<img
								src={project.img}
								alt={project.title}
								class="project-img w-full h-full object-cover grayscale-[30%] group-hover:grayscale-0 transition-all duration-700" />
							<!-- Project Number Overlay -->
							<div
								class="absolute top-0 left-0 bg-primary text-white font-mono text-xl p-4">
								{project.id}
							</div>
						</div>
					</div>

					<!-- CONTENT COLUMN -->
					<div class="lg:col-span-5 project-content">
						<div class="mb-8">
							<p
								class="font-mono text-primary text-sm uppercase mb-4 tracking-widest">
								{project.category}
							</p>
							<h2 class="text-4xl md:text-5xl lg:text-6xl leading-tight mb-6">
								{project.title}
							</h2>
							<p class="font-sans text-lg text-foreground/70 leading-relaxed mb-8">
								{project.description}
							</p>
						</div>

						<!-- Hard Metrics Grid -->
						<div
							class="grid grid-cols-2 gap-y-6 gap-x-4 mb-10 border-t border-grid pt-8">
							<div>
								<div class="flex items-center gap-2 text-foreground/50 mb-1">
									<CircleDollarSign class="w-4 h-4" />
									<p class="font-mono text-xs uppercase tracking-wider">
										Project Value
									</p>
								</div>
								<p class="font-mono text-xl md:text-2xl">{project.value}</p>
							</div>

							<div>
								<div class="flex items-center gap-2 text-foreground/50 mb-1">
									<Calendar class="w-4 h-4" />
									<p class="font-mono text-xs uppercase tracking-wider">
										Duration
									</p>
								</div>
								<p class="font-mono text-xl md:text-2xl">{project.duration}</p>
							</div>

							<div class="col-span-2">
								<div class="flex items-center gap-2 text-foreground/50 mb-1">
									<MapPin class="w-4 h-4" />
									<p class="font-mono text-xs uppercase tracking-wider">
										Location
									</p>
								</div>
								<p class="font-mono text-lg">{project.location}</p>
							</div>
						</div>

						<!-- Fake Button for aesthetic / Future Case Study Link -->
						<button
							class="flex items-center gap-2 font-display text-lg uppercase group/btn text-foreground hover:text-primary transition-colors">
							<span>View Full Case Study</span>
							<ArrowUpRight
								class="w-6 h-6 transform group-hover/btn:translate-x-1 group-hover/btn:-translate-y-1 transition-transform" />
						</button>
					</div>
				</div>
			</div>
		</article>
	{/each}
</section>

<!-- BOTTOM CTA -->
<section class="py-32 bg-foreground text-background">
	<div class="container mx-auto px-6 text-center max-w-4xl">
		<HardHat class="w-16 h-16 text-background/20 mx-auto mb-8" />
		<h2 class="text-4xl md:text-6xl mb-6">HAVE A PROJECT OF THIS SCALE?</h2>
		<p class="font-sans text-xl text-background/60 mb-10 leading-relaxed">
			Our estimation and engineering teams are ready to review your RFP. We provide detailed
			bids backed by tier-1 bonding capacity and a proven safety record.
		</p>

		<div class="flex flex-col sm:flex-row justify-center gap-6">
			<a
				href="/contact"
				class="bg-primary text-white font-display text-lg uppercase px-10 py-5 hover:bg-white hover:text-primary transition-colors flex items-center justify-center gap-2">
				Submit RFP / Tender <ArrowUpRight class="w-5 h-5" />
			</a>
		</div>
	</div>
</section>
