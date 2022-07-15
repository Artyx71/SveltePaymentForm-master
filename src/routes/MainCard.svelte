<script>
	import { t, locale, locales } from '../internationalization/i18n';
	function prettify() {
		cardNumber = cardNumber
			.replace(/[^\dA-Z]/g, '')
			.replace(/(.{4})/g, '$1 ')
			.trim();
	}

	let cardNumber = '';
	let cardYear = '';
	let cardMonth = '';
	let checkedState = false;
	let cvcCode = '';

	const getRequestURL = 'http://127.0.0.1:5000/api/cards';
	const postRequestURL = 'http://127.0.0.1:5000/api/card';
	function sendGetRequest(method, url) {
		return fetch(url);
	}
	sendGetRequest('GET', getRequestURL);

	async function sendPostRequest() {
		const res = await fetch(postRequestURL, {
			method: 'POST',
			body: JSON.stringify({
				cardNumber,
				cardYear,
				cardMonth,
				cvcCode
			})
		});

		const json = await res.json();
		result = JSON.stringify(json);
	}

	// function sendPostRequest(method, url, body = null) {
	// 	const headers = {
	// 		'Content-Type': 'application/json'
	// 	};
	// 	return fetch(url, {
	// 		method: method,
	// 		body: JSON.stringify({
	// 			cardNumber,
	// 			cardYear,
	// 			cardMonth,
	// 			cvcCode
	// 		})
	// 	});
	// }
	// sendPostRequest('POST', postRequestURL);
</script>

<main class="main__card">
	<form action="" class="main__form">
		<div class="container">
			<div class="main__card-wrapper">
				<div class="main__card-data">
					<div class="main__card-banks">
						<ul class="main__card-banks-list">
							<li class="main__card-banks-list-item">
								<img src="images/mir.png" alt="" />
							</li>
							<li class="main__card-banks-list-item">
								<img src="images/visa.png" alt="" />
							</li>
							<li class="main__card-banks-list-item">
								<img src="images/Mastercard.png" alt="" />
							</li>
							<li class="main__card-banks-list-item">
								<img src="images/maestro.png" alt="" />
							</li>
							<li class="main__card-banks-list-item">
								<img src="images/american_express.png" alt="" />
							</li>
							<li class="main__card-banks-list-item">
								<img src="images/union.png" alt="" />
							</li>
						</ul>
					</div>

					<label for="cardNums">
						<span class="main__card-span-block">{$t('homepage.cardnum-1')}</span>
						<input
							type="text"
							class="cardNumber"
							maxlength="19"
							required
							bind:value={cardNumber}
							on:input={prettify}
							pattern="[0-9]*\s[0-9]*\s[0-9]*\s[0-9]*"
						/>
						<span class="main__card-span-block">{$t('homepage.cardnum-2')}</span>
					</label>
					<label for="cardExpDate">
						<span class="main__card-span-block">{$t('homepage.cardnum-3')} </span>
						<input
							type="text"
							class="expDate"
							maxlength="2"
							placeholder="ММ"
							required
							bind:value={cardMonth}
						/>
						<span>/</span>
						<input
							type="text"
							class="expDate"
							maxlength="2"
							placeholder="ГГ"
							required
							bind:value={cardYear}
						/>
					</label>
				</div>
				<div class="main__card-cvc">
					<div class="blackline" />
					<label for="#"
						><span class="main__CVC-span-block">CVV/CVC</span>
						<input
							type="password"
							class="cvcData"
							maxlength="3"
							placeholder="000"
							required
							bind:value={cvcCode}
						/>
						<span class="main__CVC-span-block">{$t('homepage.cardback')}</span>
					</label>
				</div>
			</div>
		</div>
		<div class="container">
			<label for="cardSave">
				<input type="checkbox" bind:checked={checkedState} />
				<span
					>{$t('homepage.cardcheck-1')}
					<span class="main__card-checkbox-span-block"
						>{$t('homepage.cardcheck-2')}
						<a href="#">{$t('homepage.cardcheck-3')}</a></span
					></span
				>
			</label>

			<div class="main__card-submit container">
				<label for="cardSubmit"
					><input type="submit" on:click={sendPostRequest} value={$t('homepage.button')} /></label
				>
			</div>
		</div>
	</form>
</main>

<style></style>
