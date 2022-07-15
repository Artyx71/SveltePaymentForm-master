<script>
	import { t, locale, locales } from '../internationalization/i18n';
	import '../styles/verified.css';
</script>

<section class="info">
	<div class="container">
		<div class="info__inner">
			<div class="info__price">
				<h1>2000 Р</h1>
			</div>
			<div class="info__place">
				<p>Магазин</p>
				<p>psp</p>
			</div>
			<div class="info__card">
				<p>Номер карты</p>
				<p>** 4004</p>
			</div>
			<div class="info__date">
				<p>Дата</p>
				<p>07.07.2022</p>
			</div>
		</div>
		<div class="feedback">
			<h2>Отправили Код</h2>
			<p>Для его получения ваш номер должен быть подключен к СМС-банку</p>
		</div>
		<div class="feedback__data">
			<p>Введите код для оплаты покупки</p>
			<input name="kod" class="" autocomplete="tel-country-code" pattern="[0-9]*" type="text" />
			<p>
				Повторный запрос через
				<span style="font-weight: 700"> 19 секунд</span>
			</p>
			<input class="feedback__data-btn hide" type="submit" value="получить новый код" />

			<p class="hide">Или подключить <a href="#">СМС-банк</a></p>
		</div>
		<footer class="footer">
			<a href="#">Отменить</a>
			<a href="#">Безопасность</a>
		</footer>
	</div>
</section>

<style></style>
