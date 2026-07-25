<script lang="ts">
	import "./layout.css"
	import favicon from "$lib/assets/favicon.svg"
	import {
		Building2,
		Zap,
		HardHat,
		Phone,
		Mail,
		MapPin,
		ArrowUpRight,
		Menu,
		X,
		FileText,
		ShieldCheck,
		Download,
	} from "@lucide/svelte"

    import gsap from "gsap";
    import ScrollSmoother from "gsap/dist/ScrollSmoother";
	import { useGsap } from "$lib/utils/useGsap"

    useGsap(() => {
        gsap.registerPlugin(ScrollSmoother);

        ScrollSmoother.create({
            smooth: 2,
            effects: true,
        });
    })

	let isMobileMenuOpen = $state(false)
    
	function toggleMobileMenu() {
        isMobileMenuOpen = !isMobileMenuOpen
	}

    let { children } = $props()
</script>

<svelte:head>
	<title
		>Caribbian International Ltd. | Commercial Construction, Civil & Industrial Electrical
		Engineering</title>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;700&family=Oswald:wght@500;600;700&display=swap"
		rel="stylesheet" />
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="min-h-screen flex flex-col relative selection:bg-primary selection:text-white">
	<!-- Corporate Top Utility Bar -->
	<div
		class="bg-foreground text-background text-xs font-mono py-2.5 px-6 border-b border-white/10 hidden lg:block">
		<div class="container mx-auto flex justify-between items-center">
			<div class="flex items-center gap-8">
				<span class="flex items-center gap-2 text-white/70">
					<MapPin class="w-3.5 h-3.5 text-primary" /> Central Operations Office & Regional
					Hubs
				</span>
				<span class="flex items-center gap-2 text-white/70">
					<ShieldCheck class="w-3.5 h-3.5 text-primary" /> ISO Compliant & HSE Certified EPC
					Contractor
				</span>
			</div>
			<div class="flex items-center gap-6">
				<a
					href="mailto:procurement@caribbian.com"
					class="text-white/70 hover:text-primary transition-colors flex items-center gap-1.5">
					<Mail class="w-3.5 h-3.5" /> Bids: procurement@caribbian.com
				</a>
				<a
					href="tel:+256000000000"
					class="text-white/70 hover:text-primary transition-colors flex items-center gap-1.5">
					<Phone class="w-3.5 h-3.5" /> Direct: +256 (0) 414 000 000
				</a>
			</div>
		</div>
	</div>

	<!-- Primary Enterprise Header -->
	<header
		class="sticky top-0 bg-background/95 backdrop-blur-md border-b border-grid z-50 transition-all duration-300">
		<div class="container mx-auto px-6 h-22 flex items-center justify-between">
			<!-- Brand Logo & Identity -->
			<a href="/" class="flex items-center gap-4 group">
				<div
					class="w-12 h-12 bg-foreground group-hover:bg-primary transition-colors duration-300 flex items-center justify-center text-white font-display font-bold text-2xl tracking-tighter">
					CI
				</div>
				<div class="flex flex-col">
					<span
						class="font-display text-2xl font-bold leading-none tracking-tight text-foreground group-hover:text-primary transition-colors">
						CARIBBIAN
					</span>
					<span
						class="font-mono text-xs uppercase tracking-widest text-foreground/60 leading-tight">
						INTERNATIONAL LTD.
					</span>
				</div>
			</a>

			<!-- Desktop Navigation Links -->
			<nav class="hidden lg:flex items-center gap-10 font-sans font-medium text-sm">
				<a
					href="#services"
					class="hover:text-primary transition-colors py-2 uppercase tracking-wider text-xs font-mono"
					>Services & Disciplines</a>
				<a
					href="#projects"
					class="hover:text-primary transition-colors py-2 uppercase tracking-wider text-xs font-mono"
					>Project Portfolio</a>
				<a
					href="#safety"
					class="hover:text-primary transition-colors py-2 uppercase tracking-wider text-xs font-mono"
					>Safety & Operational Excellence</a>
				<a
					href="#subcontractors"
					class="hover:text-primary transition-colors py-2 uppercase tracking-wider text-xs font-mono"
					>Subcontractors & Partners</a>
			</nav>

			<!-- Action Callouts -->
			<div class="hidden lg:flex items-center gap-4">
				<a
					href="/company-profile.pdf"
					download
					class="border border-foreground/20 hover:border-foreground text-foreground px-5 py-3 font-mono text-xs uppercase tracking-wider flex items-center gap-2 hover:bg-foreground hover:text-white transition-all duration-300">
					<Download class="w-3.5 h-3.5" /> Capabilities PDF
				</a>
				<a
					href="#rfq"
					class="bg-primary hover:bg-primary-dark text-white font-display text-sm uppercase tracking-wider px-6 py-3 transition-colors duration-300 flex items-center gap-2">
					Request Proposal <ArrowUpRight class="w-4 h-4" />
				</a>
			</div>

			<!-- Mobile Menu Button -->
			<button
				on:click={toggleMobileMenu}
				class="lg:hidden text-foreground p-2 focus:outline-none"
				aria-label="Toggle Navigation">
				{#if isMobileMenuOpen}
					<X class="w-7 h-7" />
				{:else}
					<Menu class="w-7 h-7" />
				{/if}
			</button>
		</div>

		<!-- Mobile Dropdown Menu -->
		{#if isMobileMenuOpen}
			<div
				class="lg:hidden bg-background border-b border-grid px-6 py-8 space-y-6 animate-in slide-in-from-top duration-300">
				<nav class="flex flex-col space-y-4 font-mono text-sm uppercase tracking-wider">
					<a
						href="#services"
						on:click={toggleMobileMenu}
						class="text-foreground hover:text-primary">Services & Disciplines</a>
					<a
						href="#projects"
						on:click={toggleMobileMenu}
						class="text-foreground hover:text-primary">Project Portfolio</a>
					<a
						href="#safety"
						on:click={toggleMobileMenu}
						class="text-foreground hover:text-primary">Safety & Operations</a>
					<a
						href="#subcontractors"
						on:click={toggleMobileMenu}
						class="text-foreground hover:text-primary">Subcontractors & Partners</a>
				</nav>
				<div class="pt-6 border-t border-grid flex flex-col space-y-3">
					<a
						href="/company-profile.pdf"
						download
						class="border border-foreground text-center py-3 font-mono text-xs uppercase tracking-wider">
						Download Company Profile
					</a>
					<a
						href="#rfq"
						on:click={toggleMobileMenu}
						class="bg-primary text-white text-center py-3 font-display uppercase tracking-wider text-sm">
						Request Proposal / Bid
					</a>
				</div>
			</div>
		{/if}
	</header>

	<!-- Main Viewport -->
	<main class="flex-grow">
		{@render children()}
	</main>
	<!-- Global Enterprise Corporate Footer (Turner/Kiewit Architecture) -->
	<footer
		class="bg-foreground text-background pt-24 pb-12 border-t-8 border-primary relative overflow-hidden">
		<div class="container mx-auto px-6">
			<div
				class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-12 pb-16 border-b border-white/10">
				<!-- Col 1: Brand Info -->
				<div class="lg:col-span-2 space-y-6">
					<div class="flex items-center gap-3">
						<div
							class="w-10 h-10 bg-primary text-white font-display font-bold text-xl flex items-center justify-center">
							CI
						</div>
						<span class="font-display text-2xl text-white tracking-wider"
							>CARIBBIAN INTERNATIONAL</span>
					</div>
					<p class="font-sans text-white/70 text-base leading-relaxed max-w-md">
						Delivering major commercial building developments, high-capacity industrial
						power grids, and vital civil infrastructure across regional commercial hubs.
					</p>
					<div class="font-mono text-xs text-white/40 space-y-1">
						<p>REGISTRATION NO: REG-2014-998271</p>
						<p>VAT TIN REGISTERED • PUBLIC WORK CERTIFIED</p>
					</div>
				</div>

				<!-- Col 2: Core Services -->
				<div class="space-y-4">
					<h3 class="font-mono text-xs uppercase tracking-widest text-primary">
						Core Disciplines
					</h3>
					<ul class="space-y-2.5 font-sans text-sm text-white/70">
						<li>
							<a href="#services" class="hover:text-primary transition-colors"
								>Industrial Electrical Systems</a>
						</li>
						<li>
							<a href="#services" class="hover:text-primary transition-colors"
								>Commercial Construction</a>
						</li>
						<li>
							<a href="#services" class="hover:text-primary transition-colors"
								>Civil Infrastructure & Roads</a>
						</li>
						<li>
							<a href="#services" class="hover:text-primary transition-colors"
								>Substation & Grid Setup</a>
						</li>
						<li>
							<a href="#services" class="hover:text-primary transition-colors"
								>Heavy Earthworks & Paving</a>
						</li>
					</ul>
				</div>

				<!-- Col 3: Bidding & Governance -->
				<div class="space-y-4">
					<h3 class="font-mono text-xs uppercase tracking-widest text-primary">
						Governance & Bids
					</h3>
					<ul class="space-y-2.5 font-sans text-sm text-white/70">
						<li>
							<a href="#safety" class="hover:text-primary transition-colors"
								>HSE Safety Policy</a>
						</li>
						<li>
							<a href="#subcontractors" class="hover:text-primary transition-colors"
								>Subcontractor Portal</a>
						</li>
						<li>
							<a href="#rfq" class="hover:text-primary transition-colors"
								>Tender Document Submission</a>
						</li>
						<li>
							<a
								href="/company-profile.pdf"
								download
								class="hover:text-primary transition-colors"
								>Capability Statement PDF</a>
						</li>
						<li>
							<a href="#safety" class="hover:text-primary transition-colors"
								>Quality Assurance Protocol</a>
						</li>
					</ul>
				</div>

				<!-- Col 4: Corporate Offices -->
				<div class="space-y-4">
					<h3 class="font-mono text-xs uppercase tracking-widest text-primary">
						Headquarters
					</h3>
					<div class="space-y-3 font-sans text-sm text-white/70">
						<p class="flex items-start gap-2">
							<MapPin class="w-4 h-4 text-primary shrink-0 mt-0.5" />
							<span>Plot 48, Industrial Area Sector 2, Central District, Uganda</span>
						</p>
						<p class="flex items-center gap-2">
							<Phone class="w-4 h-4 text-primary shrink-0" />
							<span>+256 (0) 414 000 000</span>
						</p>
						<p class="flex items-center gap-2">
							<Mail class="w-4 h-4 text-primary shrink-0" />
							<span>bids@caribbian.com</span>
						</p>
					</div>
				</div>
			</div>

			<!-- Footer Bottom Copyright & Legal -->
			<div
				class="pt-8 flex flex-col md:flex-row items-center justify-between font-mono text-xs text-white/40 gap-4">
				<p>
					© {new Date().getFullYear()} Caribbian International Ltd. All Rights Reserved.
				</p>
				<div class="flex gap-6">
					<a href="#" class="hover:text-white transition-colors">Terms of Compliance</a>
					<a href="#" class="hover:text-white transition-colors">Privacy Standard</a>
					<a href="#" class="hover:text-white transition-colors">Site Index</a>
				</div>
			</div>
		</div>
	</footer>
</div>
