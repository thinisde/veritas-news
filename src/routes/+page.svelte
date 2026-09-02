<script lang="ts">
	import {
		ArrowDownRight,
		ArrowRight,
		Check,
		Clock3,
		Globe2,
		Layers3,
		Link2,
		Menu,
		Network,
		Quote,
		Search,
		ShieldCheck
	} from '@lucide/svelte';

	const reports = [
		{ source: 'Source 01', title: 'Rail strike begins across the region', time: '08:12' },
		{ source: 'Source 02', title: 'Reduced services announced for commuters', time: '09:34' },
		{
			source: 'Source 03',
			title: 'Negotiations restart as disruption continues',
			time: '10:46'
		}
	];

	let signupEmail = $state('');
	let signupComplete = $state(false);

	function submitSignup(event: SubmitEvent) {
		event.preventDefault();
		signupComplete = true;
	}

	function resetSignup() {
		signupEmail = '';
		signupComplete = false;
	}

	const steps = [
		{
			number: '01',
			icon: Globe2,
			title: 'Public information',
			text: 'Veritas obtains information from the public internet.',
			output: 'Independent reports ready to compare'
		},
		{
			number: '02',
			icon: Layers3,
			title: 'Cluster the story',
			text: 'A complex clustering algorithm compares meaning, time, context, and shared entities to group reports about the same real-world story—even when their wording differs.',
			output: 'Many reports become one event'
		},
		{
			number: '03',
			icon: Quote,
			title: 'Extract the claims',
			text: 'Individual factual claims are extracted from every report, then mapped to show agreement, added context, missing details, and conflicting statements.',
			output: 'A structured claim map'
		},
		{
			number: '04',
			icon: Network,
			title: 'Track the entities',
			text: 'People, organizations, places, and events are tracked across time. New claims update the event and reveal how it connects to what happened before and after.',
			output: 'A living, connected event graph'
		}
	];
</script>

<svelte:head>
	<title>Veritas News — Too much news. One clear story.</title>
	<meta
		name="description"
		content="Veritas combines reporting from around the world into connected, evolving events so you can understand more while consuming less."
	/>
</svelte:head>

<main>
	<header class="site-header">
		<a class="header-logo" href="#top" aria-label="Veritas News home">
			<img src="/logo.svg" alt="" />
		</a>
		<nav class="header-nav" aria-label="Primary navigation">
			<a href="#how">How it works</a>
			<a href="#connect">Event graph</a>
			<a href="#compare">Compare sources</a>
		</nav>
		<a class="header-cta h-11 rounded-full bg-ink px-5 text-paper hover:bg-brand" href="#access">
			Get early access
		</a>
		<Menu class="mobile-menu" aria-label="Open navigation" />
	</header>

	<section id="top" class="hero shell">
		<div class="hero-copy">
			<p class="eyebrow"><span></span> News without the overload</p>
			<h1>
				Too much news.
				<em>One clear story.</em>
			</h1>
			<p class="hero-deck">
				Veritas combines reporting about the same story into one evolving event—so you can
				understand more while consuming less.
			</p>
			<div class="hero-actions">
				<a class="primary-button h-12 rounded-full px-6" href="#how">
					See how it works <ArrowDownRight />
				</a>
				<span class="hero-note">Less noise. More context.</span>
			</div>
		</div>

		<div class="combine-demo" aria-label="Multiple reports combined into one event">
			<div class="reports-side">
				<div class="demo-heading">
					<span>Information overload</span>
					<small>3 of 18 reports</small>
				</div>
				<div class="report-stack">
					{#each reports as report, index (report.source)}
						<article class="report-card" style:--index={index}>
							<div>
								<span>{report.source}</span>
								<time>{report.time}</time>
							</div>
							<p>{report.title}</p>
						</article>
					{/each}
				</div>
			</div>

			<div class="combine-mark" aria-hidden="true">
				<span><ArrowRight /></span>
				<small>Veritas combines</small>
			</div>

			<article class="event-card">
				<div class="event-top">
					<span><i></i> One event</span>
					<small>Live</small>
				</div>
				<div class="event-content">
					<p class="event-category">Transport · Europe</p>
					<h2>Regional rail strike enters third day</h2>
					<p>Negotiations resume as operators publish a reduced schedule.</p>
				</div>
				<div class="event-footer">
					<span><Layers3 /> 18 sources</span>
					<span><Clock3 /> Updated 8m ago</span>
				</div>
			</article>
		</div>
	</section>

	<section class="problem-section">
		<div class="shell problem-inner">
			<p class="section-label">The problem</p>
			<h2>
				More information<br />
				<em>does not mean</em><br />
				more understanding.
			</h2>
			<div class="problem-copy">
				<p>
					Every day, hundreds of headlines compete for your attention. The same story is repeated
					until information becomes noise.
				</p>
				<div class="problem-line"><span></span> Your attention is valuable.</div>
			</div>
		</div>
	</section>

	<section id="how" class="how-section shell">
		<div class="section-heading">
			<p class="section-label">How Veritas works</p>
			<div class="how-heading-copy">
				<h2>
					From scattered reports<br />
					to <em>structured understanding.</em>
				</h2>
				<p>
					Behind every clear event is a multi-stage intelligence system that organizes the public
					information, separates what is being claimed, and keeps the people, places, organizations,
					and events connected over time.
				</p>
			</div>
		</div>

		<figure class="process-figure">
			<div class="process-image-wrap">
				<img
					src="/veritas-process.png"
					alt="Documents from the public internet flowing into story clusters, extracted claims, and a connected entity graph"
					width="1832"
					height="859"
					loading="lazy"
					decoding="async"
				/>
			</div>
			<figcaption>
				<span><i>01</i> Public internet</span>
				<span><i>02</i> Story clusters</span>
				<span><i>03</i> Claim map</span>
				<span><i>04</i> Entity graph</span>
			</figcaption>
		</figure>

		<div class="steps-grid">
			{#each steps as step (step.number)}
				<article class="step-card">
					<div class="step-top">
						<span>{step.number}</span>
						<step.icon />
					</div>
					<h3>{step.title}</h3>
					<p>{step.text}</p>
					<div class="step-output">
						<small>Produces</small>
						<strong>{step.output}</strong>
					</div>
				</article>
			{/each}
		</div>
	</section>

	<section id="connect" class="graph-section">
		<div class="shell graph-inner">
			<div class="graph-copy">
				<p class="section-label light">Beyond one story</p>
				<h2>Events do not happen alone.</h2>
				<p>Veritas tracks what happens next and links related events into a knowledge graph.</p>
				<ul>
					<li><Check /> Follow a story through time</li>
					<li><Check /> Discover related people and places</li>
					<li><Check /> See how one event leads to another</li>
				</ul>
			</div>

			<div class="knowledge-graph" aria-label="Connected Veritas event graph">
				<div class="graph-grid"></div>
				<svg viewBox="0 0 640 480" aria-hidden="true">
					<path d="M108 146 C190 146 192 238 280 238"></path>
					<path d="M112 344 C194 344 186 252 280 244"></path>
					<path d="M358 238 C438 238 432 124 522 124"></path>
					<path d="M358 248 C440 260 432 365 532 365"></path>
					<path class="active-path" d="M108 146 C190 146 192 238 280 238 C438 238 432 124 522 124"
					></path>
				</svg>
				<div class="graph-node node-one">
					<small>Earlier event</small>
					<strong>Strike announced</strong>
					<span>Aug 27</span>
				</div>
				<div class="graph-node node-two">
					<small>Current event</small>
					<strong>Regional disruption</strong>
					<span>18 sources</span>
				</div>
				<div class="graph-node node-three">
					<small>Related event</small>
					<strong>Talks resume</strong>
					<span>Developing</span>
				</div>
				<div class="graph-node node-four">
					<small>Entity</small>
					<strong>Rail Union</strong>
					<span>12 events</span>
				</div>
				<div class="graph-node node-five">
					<Link2 />
					<strong>Knowledge graph</strong>
				</div>
			</div>
		</div>
	</section>

	<section id="compare" class="compare-section shell">
		<div class="compare-copy">
			<p class="section-label">Compare and verify</p>
			<h2>
				Do not trust<br />
				only one source.
			</h2>
			<p>
				Compare what different outlets report, find missing context, and double-check claims before
				you believe or share them.
			</p>
			<div class="verify-pill"><ShieldCheck /> Built to help you verify information</div>
		</div>

		<div class="source-compare" aria-label="Comparison of reporting from three sources">
			<div class="compare-question">
				<span>Claim being checked</span>
				<strong>“Limited rail service will continue during the strike.”</strong>
			</div>
			<div class="source-row confirmed">
				<div class="source-icon">A</div>
				<div>
					<span>Source A</span>
					<strong>Confirms limited service</strong>
				</div>
				<small><Check /> Agrees</small>
			</div>
			<div class="source-row context">
				<div class="source-icon">B</div>
				<div>
					<span>Source B</span>
					<strong>Adds affected regions</strong>
				</div>
				<small><Search /> Context</small>
			</div>
			<div class="source-row unverified">
				<div class="source-icon">C</div>
				<div>
					<span>Source C</span>
					<strong>Does not cite the operator</strong>
				</div>
				<small><ShieldCheck /> Check</small>
			</div>
			<div class="compare-result">
				<span><Check /></span>
				<div>
					<small>Veritas summary</small>
					<strong>Supported, with regional limitations.</strong>
				</div>
			</div>
		</div>
	</section>

	<section id="access" class="final-cta">
		<div class="shell cta-inner">
			<p class="eyebrow light"><span></span> Veritas News</p>
			<h2>
				News should make you clearer,<br />
				<em>not more overwhelmed.</em>
			</h2>

			{#if signupComplete}
				<div class="signup-confirmation" role="status" aria-live="polite">
					<span><Check /></span>
					<div>
						<small>Early access requested</small>
						<strong>We will send Veritas updates to {signupEmail}.</strong>
					</div>
					<button type="button" onclick={resetSignup}>Use another email</button>
				</div>
			{:else}
				<form class="signup-form" onsubmit={submitSignup}>
					<label for="early-access-email">Your email address</label>
					<div class="signup-field">
						<input
							id="early-access-email"
							name="email"
							type="email"
							placeholder="you@example.com"
							autocomplete="email"
							bind:value={signupEmail}
							required
						/>
						<button type="submit">Request early access <ArrowRight /></button>
					</div>
					<p>Occasional product updates only. Unsubscribe at any time.</p>
				</form>
			{/if}
		</div>
	</section>

	<footer class="site-footer shell">
		<a class="wordmark" href="#top">Ve<span>.</span></a>
		<p>One event. Every source. Full context.</p>
		<span>© 2026 Veritas News</span>
	</footer>
</main>
