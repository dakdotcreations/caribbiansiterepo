<script lang="ts">
	import { ArrowUpRight, Mail, MapPin, Phone, Send, ShieldCheck } from "@lucide/svelte"
</script>

<svelte:head>
	<title>Contact | Caribbian International Ltd.</title>
	<meta
		name="description"
		content="Contact Caribbian International Ltd. at our Ntinda Industrial Area office in Kampala." />
</svelte:head>

<section
	class="relative overflow-hidden bg-foreground text-white bg-blueprint border-b-8 border-primary">
	<div
		class="absolute inset-y-0 right-0 hidden w-1/2 -skew-x-12 translate-x-32 bg-primary/10 lg:block">
	</div>
	<div class="container relative z-10 mx-auto px-6 py-20 md:py-28">
		<p class="mb-5 font-mono text-xs uppercase tracking-[0.24em] text-primary">
			Operations Office / Kampala
		</p>
		<h1 class="max-w-4xl text-6xl font-bold leading-none text-white md:text-8xl">
			START THE<br /><span class="text-primary">CONVERSATION.</span>
		</h1>
		<p class="mt-7 max-w-2xl text-lg font-light leading-relaxed text-white/75 md:text-xl">
			Bring us your next commercial, civil, or industrial electrical requirement. Our team is
			ready to discuss scope, schedule, and delivery.
		</p>
	</div>
</section>

<section class="bg-background py-16 md:py-24">
	<div class="container mx-auto grid gap-12 px-6 lg:grid-cols-12 lg:gap-16">
		<div class="lg:col-span-5">
			<p class="font-mono text-xs uppercase tracking-[0.2em] text-primary">Find Us</p>
			<h2 class="mt-3 text-4xl font-bold leading-none md:text-5xl">OUR OFFICE</h2>

			<div
				class="mt-8 border-l-4 border-primary bg-foreground p-7 text-white shadow-xl shadow-foreground/10">
				<div class="flex items-start gap-4">
					<MapPin class="mt-1 h-5 w-5 shrink-0 text-primary" aria-hidden="true" />
					<address class="not-italic">
						<p class="font-display text-2xl uppercase">Caribbian International Ltd.</p>
						<p class="mt-4 font-mono text-sm leading-7 text-white/75">
							Plot No. M220, Ntinda Industrial Area<br />
							Nakawa Division<br />
							P.O. Box 3172<br />
							Kampala, Uganda
						</p>
					</address>
				</div>
			</div>

			<div class="mt-6 grid gap-3 sm:grid-cols-2">
				<!-- <a href="mailto:contact@caribbianinternational.com" class="group flex items-center justify-between border border-foreground/15 bg-white px-5 py-4 transition-colors hover:border-primary hover:bg-primary hover:text-white">
					<span><span class="block font-mono text-[10px] uppercase tracking-widest text-foreground/50 group-hover:text-white/70">Email</span><span class="mt-1 block text-sm font-medium">contact@caribbianinternational.com</span></span>
					<Mail class="ml-3 h-5 w-5 shrink-0 text-primary group-hover:text-white" aria-hidden="true" />
				</a> -->
				<a
					href="tel:+256740000000"
					class="group flex items-center justify-between border border-foreground/15 bg-white px-5 py-4 transition-colors hover:border-primary hover:bg-primary hover:text-white">
					<span
						><span
							class="block font-mono text-[10px] uppercase tracking-widest text-foreground/50 group-hover:text-white/70"
							>Direct Line</span
						><span class="mt-1 block text-sm font-medium">+256 (740) 000 000</span
						></span>
					<Phone
						class="ml-3 h-5 w-5 shrink-0 text-primary group-hover:text-white"
						aria-hidden="true" />
				</a>
			</div>

			<div
				class="mt-9 flex items-center gap-3 border-t border-grid pt-6 font-mono text-xs leading-relaxed text-foreground/60">
				<ShieldCheck class="h-5 w-5 shrink-0 text-primary" aria-hidden="true" />
				<span
					>Commercial construction, industrial power, and civil infrastructure enquiries.</span>
			</div>
		</div>

		<div class="lg:col-span-7" id="enquiry">
			<div
				class="border border-foreground/15 bg-white p-6 shadow-2xl shadow-foreground/5 md:p-10">
				<div class="flex items-start justify-between gap-6 border-b border-grid pb-6">
					<div>
						<p class="font-mono text-xs uppercase tracking-[0.2em] text-primary">
							Project Enquiry
						</p>
						<h2 class="mt-2 text-4xl font-bold leading-none">TELL US WHAT YOU NEED.</h2>
					</div>
					<Send class="h-7 w-7 shrink-0 text-primary" aria-hidden="true" />
				</div>

				<form
					action="mailto:contact@caribbianinternational.com"
					method="post"
					enctype="text/plain"
					class="mt-8 space-y-6">
					<div class="grid gap-6 md:grid-cols-2">
						<label class="block">
							<span
								class="font-mono text-xs font-medium uppercase tracking-wider text-foreground/70"
								>Full name</span>
							<input
								name="name"
								required
								autocomplete="name"
								class="mt-2 w-full border border-foreground/20 bg-background px-4 py-3 text-foreground outline-none transition-colors placeholder:text-foreground/35 focus:border-primary focus:ring-1 focus:ring-primary"
								placeholder="Your name" />
						</label>
						<label class="block">
							<span
								class="font-mono text-xs font-medium uppercase tracking-wider text-foreground/70"
								>Company</span>
							<input
								name="company"
								autocomplete="organization"
								class="mt-2 w-full border border-foreground/20 bg-background px-4 py-3 text-foreground outline-none transition-colors placeholder:text-foreground/35 focus:border-primary focus:ring-1 focus:ring-primary"
								placeholder="Company or organisation" />
						</label>
					</div>
					<div class="grid gap-6 md:grid-cols-2">
						<label class="block">
							<span
								class="font-mono text-xs font-medium uppercase tracking-wider text-foreground/70"
								>Email address</span>
							<input
								name="email"
								type="email"
								required
								autocomplete="email"
								class="mt-2 w-full border border-foreground/20 bg-background px-4 py-3 text-foreground outline-none transition-colors placeholder:text-foreground/35 focus:border-primary focus:ring-1 focus:ring-primary"
								placeholder="you@company.com" />
						</label>
						<label class="block">
							<span
								class="font-mono text-xs font-medium uppercase tracking-wider text-foreground/70"
								>Phone number</span>
							<input
								name="phone"
								type="tel"
								autocomplete="tel"
								class="mt-2 w-full border border-foreground/20 bg-background px-4 py-3 text-foreground outline-none transition-colors placeholder:text-foreground/35 focus:border-primary focus:ring-1 focus:ring-primary"
								placeholder="+256 ..." />
						</label>
					</div>
					<label class="block">
						<span
							class="font-mono text-xs font-medium uppercase tracking-wider text-foreground/70"
							>Project discipline</span>
						<select
							name="project_discipline"
							required
							class="mt-2 w-full border border-foreground/20 bg-background px-4 py-3 text-foreground outline-none transition-colors focus:border-primary focus:ring-1 focus:ring-primary">
							<option value="" disabled selected>Select a discipline</option>
							<option>Commercial Construction</option>
							<option>Industrial Electrical Systems</option>
							<option>Civil Infrastructure</option>
							<option>General Enquiry</option>
						</select>
					</label>
					<label class="block">
						<span
							class="font-mono text-xs font-medium uppercase tracking-wider text-foreground/70"
							>Project brief</span>
						<textarea
							name="project_brief"
							required
							rows="5"
							class="mt-2 w-full resize-y border border-foreground/20 bg-background px-4 py-3 text-foreground outline-none transition-colors placeholder:text-foreground/35 focus:border-primary focus:ring-1 focus:ring-primary"
							placeholder="Tell us about the scope, location, timeline, or technical requirements."
						></textarea>
					</label>
					<div
						class="flex flex-col gap-4 border-t border-grid pt-6 sm:flex-row sm:items-center sm:justify-between">
						<p
							class="max-w-sm font-mono text-[11px] leading-relaxed text-foreground/55">
							Submitting opens your default email application with this enquiry
							addressed to our team.
						</p>
						<button
							type="submit"
							class="inline-flex items-center justify-center gap-3 bg-primary px-6 py-4 font-display text-base uppercase tracking-wider text-white transition-colors hover:bg-primary-dark focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
							Submit <ArrowUpRight class="h-5 w-5" aria-hidden="true" />
						</button>
					</div>
				</form>
			</div>
		</div>
	</div>
</section>
