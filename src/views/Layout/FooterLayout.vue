<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__container">
        <div class="row">
          <div class="col-12 col-lg-4">
            <img class="footer__logo" src="/images/logo.svg" alt="">
          </div>
          <div class="col-12 col-lg-6">
            <div class="footer__links-container">
              <div class="footer__menu">
                <footer-nav :data="footerMenu"/>
              </div>
              <div class="footer__social">
                <footer-nav :data="socialList"/>
              </div>
            </div>
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
  z-index: 2;
  padding-top: 100px;

  &:before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url(/images/footer.png);
    background-repeat: no-repeat;
    background-position: 50% 100%;
    z-index: -1;
  }
  
  &__container {
    padding: 60px 120px;
    border-radius: 60px 60px 0 0;
    border: 2px solid #6B6B6B;
    border-bottom: none;
    backdrop-filter: blur(11px);
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

    @media (max-width: 768px) {
      gap: 20px;
      flex-direction: column;
    }
  }
}
</style>
