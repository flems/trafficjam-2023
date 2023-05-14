<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__container">
        <div class="row">
          <div class="col-12 col-md-6 col-lg-3">
            <div class="footer__logo-wrapper">
              <img class="footer__logo" src="/images/logo.svg" alt="">
              <p class="footer__copyright">©️ 2023 Rafinad  ИНН 561654684</p>
            </div>
          </div>
          <div class="col-12 col-md-6 col-lg-8 offset-lg-1">
            <div class="footer__links-container">
              <div class="footer__nav">
                <p class="footer__title">Документация</p>
                <footer-nav :data="footerMenu"/>
              </div>
              <div class="footer__nav">
                <p class="footer__title">Наши социальные сети</p>
                <footer-nav :data="socialList"/>
              </div>
            </div>
            <p class="footer__copyright footer__copyright--mobile">©️ 2023 Rafinad  ИНН 561654684</p>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import FooterNav from '@/components/FooterNav'

const footerMenu = [
  {
    link: '#',
    name: 'Публичная оферта'
  },
  {
    link: '#',
    name: 'Лицензия сайта'
  },
  {
    link: '#',
    name: 'Политика конфиденциальности'
  },
  {
    link: '#',
    name: 'Вопрос-ответ'
  }
]

const socialList = [
  {
    link: '#',
    name: 'Telegram',
    icon: '/images/icons/telegram.svg'
  },
  {
    link: '#',
    name: 'Вконтакте',
    icon: '/images/icons/vk.svg'
  },
  {
    link: '#',
    name: 'TenChat',
    icon: '/images/icons/tenchat.svg'
  },
  {
    link: '#',
    name: 'Та самая соцсеть',
    icon: '/images/icons/inst.svg'
  }
]
</script>

<style lang="scss">
.footer {
  border-bottom: none;
  position: relative;
  z-index: 1;
  padding-top: 100px;

  // &:before {
  //   content: '';
  //   position: absolute;
  //   bottom: 0;
  //   left: 0;
  //   width: 100%;
  //   padding-top: 40%;
  //   background-image: url('/images/footer.png');
  //   background-repeat: no-repeat;
  //   background-position: 50% 100%;
  //   z-index: -1;
  // }

  &__logo-wrapper {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    height: 100%;
    justify-content: space-between;
  }

  &__copyright {
    font-size: 16px;
    color: #6B6B6B;

    @media (max-width: 768px) {
      display: none;
    }

    &--mobile {
      display: none;

      @media (max-width: 768px) {
        display: block;
        margin-top: 20px;
      }
    }
  }

  &__nav {
    max-width: 260px;
  }

  &__title {
    font-family: 'Unbounded', sans-serif;
    font-weight: 500;
    font-size: 16px;
    line-height: 1.4;
    text-transform: uppercase;
    color: #6B6B6B;
    padding-bottom: 20px;
  }
  
  &__container {
    padding: 60px 8%;
    border-radius: 60px 60px 0 0;
    border: 2px solid #6B6B6B;
    border-bottom: none;
    backdrop-filter: blur(11px);

    @media (max-width: 992px) {
      padding: 40px;
    }
  }

  &__logo {
    img {
      width: 124px;
      display: block;
    }
  }

  &__links-container {
    display: flex;
    gap: 160px;
    
    @media (max-width: 1440px) {
      gap: 90px;
    }

    @media (max-width: 992px) {
      flex-direction: column;
      gap: 32px;
    }

    @media (max-width: 768px) {
      gap: 20px;
      flex-direction: column;
    }
  }
}
</style>
