<script>
	import { t, locale, locales } from '../internationalization/i18n';
	let cardValue = Math.ceil(Math.random() * 1500) + ' ' + 'Р';
</script>

<p>
	<select bind:value={$locale}>
		{#each locales as l}
			<option value={l}>{l}</option>
		{/each}
	</select>
</p>

<header class="header">
	<div class="container">
		<div class="header__inner">
			<h2>{$t('homepage.title')}</h2>
			<h2>{cardValue}</h2>
		</div>
	</div>
</header>
<section class="addcard">
	<div class="container">
		<div class="addcard__wrapper">
			<div class="add__new-card">
				<a href="#">
					<img src="images/addCard.png" alt="addCardIcon" />
					<p class="add__new-card-text">{$t('Usercard.newcard')}</p>
				</a>
			</div>
		</div>
	</div>
</section>

<style></style>
