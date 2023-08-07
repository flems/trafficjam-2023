<template>
  <div class="sponsors">
    <div class="container">
      <h2>Спонсоры проекта</h2>

      <div class="row">
        <div class="col-12 col-xl-6 col-lg-7">
          <card
            logo="/images/logos/tinkoff.svg"
            title="Тинькофф"
            tag-icon="universe"
            theme="blue"
            full-height
            tag-name="Вселенная"
          >
            <template v-slot:content>
              <div class="sponsors__content">
                <div>
                  Космическая выгода для всех участников TrafficJam 2023! Не просто красивые карты, могут экономить и зарабатывать для вас!
                </div>
                <a href="https://rafinad.io/offers/?term=%D1%82%D0%B8%D0%BD%D1%8C%D0%BA%D0%BE%D1%84%D1%84&page=1&page_size=10&sortField=publish_dt&sortDir=desc" class="sponsors__link" target="_blank">
                  <span>Пристыковаться</span>
                </a>
              </div>
            </template>
          </card>
        </div>
        <div class="col-12 col-xl-6 col-lg-7">
          <card
            logo="/images/logos/alpha.png"
            title="Альфа Банк"
            tag-icon="galaxy"
            theme="blue"
            full-height
            tag-name="Галактика"
          >
            <template v-slot:content>
              <div class="sponsors__content">
                <div>
                  Лучший мобильный банк по версии Markswebb
                </div>
                <!-- <a href="" class="sponsors__link" target="_blank">
                  <span>Пристыковаться</span>
                </a> -->
              </div>
            </template>
          </card>
        </div>
        <div class="col-12 col-xl-5 col-md-6">
          <card
            logo="/images/logos/placeholder-logo-invert.svg"
            title=""
            tag-icon="planet"
            theme="black"
            full-height
            tag-name="Планета"
          >
            <template v-slot:content>
              <div class="sponsors__content">
                <div>
                  Скоро сюда прибудет гость межгалактического альянса. Ожидаем.
                </div>
                <!-- <a href="" class="sponsors__link" target="_blank">
                  <span>Пристыковаться</span>
                </a> -->
              </div>
            </template>
          </card>
        </div>
        <div class="col-12 col-md-6 col-xl-5">
          <card
            logo="/images/logos/gazprom.png"
            title="Газпромбанк"
            tag-icon="planet"
            theme="black"
            full-height
            tag-name="Планета"
          >
            <template v-slot:content>
              <div class="sponsors__content">
                <div>
                  Один из крупнейших универсальных финансовых институтов России, предоставляющий широкий спектр продуктов и услуг корпоративным и частным клиентам, финансовым институтам, институциональным и частным инвесторам.
                </div>
                <a href="https://rafinad.io/offers/?term=%D0%B3%D0%B0%D0%B7%D0%BF%D1%80%D0%BE%D0%BC%D0%B1%D0%B0%D0%BD%D0%BA&page=1&page_size=10&sortField=publish_dt&sortDir=desc" class="sponsors__link" target="_blank">
                  <span>Пристыковаться</span>
                </a>
              </div>
            </template>
          </card>
        </div>
        <div class="col-12 col-xl-7 col-lg-10 col-md-12">
          <div class="row">
            <div class="col-12 col-md-6">
              <card
                logo="/images/logos/Logo_white.png"
                title="Вэббанкир"
                tag-icon="star"
                theme="black"
                full-height
                tag-name="Звезда"
              >
                <template v-slot:content>
                  <div class="sponsors__content">
                    <div>
                      Мы стали первыми в нашей стране в выдаче денег по технологии p2p, первыми начали работать с картами «Мир» и постоянно завоевываем множество престижных финансовых премий и наград.
                    </div>
                    <a href="https://rafinad.io/offers/?term=webbankir&page=1&page_size=10&sortField=publish_dt&sortDir=desc" class="sponsors__link" target="_blank">
                      <span>Пристыковаться</span>
                    </a>
                  </div>
                </template>
              </card>
            </div>
            <div class="col-12 col-md-6">
              <card
                logo="/images/logos/rosbank.png"
                title="Росбанк"
                tag-icon="star"
                theme="black"
                full-height
                tag-name="Звезда"
              >
                <template v-slot:content>
                  <div class="sponsors__content">
                    <div>
                      30 лет мы не стоим на месте и постоянно улучшаем качество наших продуктов, один из которых — кредитная карта #120наВСЁ Плюс. Желаем участникам конкурса успехов в продвижении и космического апрува.
                    </div>
                    <a href="https://rafinad.io/offers/?term=%D1%80%D0%BE%D1%81%D0%B1%D0%B0%D0%BD%D0%BA&page=1&page_size=10&sortField=publish_dt&sortDir=desc" class="sponsors__link" target="_blank">
                      <span>Пристыковаться</span>
                    </a>
                  </div>
                </template>
              </card>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import Card from "@/components/Card"
</script>

<style lang="scss">
.sponsors {
  .card {
    min-height: 398px;

    @media (max-width: 1199px) {
      min-height: 330px;
    }

    @media (max-width: 768px) {
      min-height: 260px;
    }
  }

  &__link {
    text-decoration: none;
    color: currentColor;
    display: block;
    width: max-content;
    margin-top: 48px;
    font-size: 16px;
    font-weight: 500;
    margin-left: auto;
    position: relative;
    padding-bottom: 2px;

    
    &:before,
    &:after {
      content: '';
      height: 1px;
      position: absolute;
      width: 100%;
      bottom: 0;
      display: block;
      left: 0;
      background: currentColor;
      border-radius: 2px;
      transition: width 0.2s ease-in;
      opacity: 0.3;
    }

    &:after {
      width: 0%;
      background: currentColor;
      left: 50%;
      opacity: 1;
      transform: translateX(-50%);
    }

    &:hover {
      &:after {
        width: 100%;
      }
    }
  }

  &__content {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex-grow: 1;
  }
}
</style>