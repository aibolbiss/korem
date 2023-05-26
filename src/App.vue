<script setup>
import TabMenu from 'primevue/tabmenu'
import Button from 'primevue/button'
import DataTable from 'primevue/datatable'
import Column from 'primevue/column'
import Chart from 'primevue/chart'
import { verticalBar, doughnut, setChartOptions } from './charts/setChart'
import { ref, reactive, onMounted } from 'vue'

const items = reactive([
  {
    label: 'Дэшборды',
    icon: 'pi pi-fw pi-home',
    to: '/'
  },
  {
    label: 'Цифровой паспорт',
    icon: 'pi pi-fw pi-calendar',
    to: '/calendar'
  },
  {
    label: 'Журналы',
    icon: 'pi pi-fw pi-pencil',
    to: '/edit'
  },
  {
    label: 'Согласование планов ремонта',
    icon: 'pi pi-fw pi-file',
    to: '/documentation'
  },
  {
    label: 'Тариф',
    icon: 'pi pi-fw pi-cog',
    to: '/settings'
  },
  {
    label: 'Сотрудники',
    icon: 'pi pi-fw pi-cog',
    to: '/settings'
  },
  {
    label: 'Настройки',
    icon: 'pi pi-fw pi-cog',
    to: '/settings'
  }
])

const technicalEconomicIndicators = reactive([
  {
    id: 1,
    number: 1,
    name_indicators: 'Установленная электрическая мощность',
    unit: 'МВт',
    y2017: '372,5',
    y2018: '372,5',
    y2019: '372,5',
    y2020: '372,5',
    y2021: '372,5'
  },
  {
    id: 2,
    number: 2,
    name_indicators: 'Располагаемая электрическая мощность',
    unit: 'МВт',
    y2017: '268,8',
    y2018: '327,8',
    y2019: '320,7',
    y2020: '320,8',
    y2021: '320,9'
  },
  {
    id: 3,
    number: 3,
    name_indicators: 'Установленная тепловая мощность',
    unit: 'Гкал',
    y2017: '881,7',
    y2018: '868,9',
    y2019: '859,9',
    y2020: '859,9',
    y2021: '859,9'
  },
  {
    id: 4,
    number: 4,
    name_indicators: 'Располагаемая тепловая мощность',
    unit: 'Гкал',
    y2017: '881,7',
    y2018: '868,9',
    y2019: '859,9',
    y2020: '859,9',
    y2021: '859,9'
  },
  {
    id: 5,
    number: 5,
    name_indicators: 'Выработка электрической энергии',
    unit: 'млн.кВтч',
    y2017: '1751,6',
    y2018: '1801,6',
    y2019: '2192,6',
    y2020: '2247,0',
    y2021: '2168,3'
  },
  {
    id: 6,
    number: 6,
    name_indicators: 'Отпуск электрической энергии',
    unit: 'млн.кВтч',
    y2017: '1464,3',
    y2018: '1499,0',
    y2019: '1852,0',
    y2020: '1901,3',
    y2021: '1825,1'
  },
  {
    id: 7,
    number: 7,
    name_indicators: 'Выработка тепловой энергии',
    unit: 'тыс. Гкал',
    y2017: '2560,0',
    y2018: '2681,6',
    y2019: '2603,8',
    y2020: '2556,2',
    y2021: '2630,0'
  },
  {
    id: 8,
    number: 8,
    name_indicators: 'Отпуск тепловой энергии',
    unit: 'тыс. Гкал',
    y2017: '2449,2',
    y2018: '2555,0',
    y2019: '2479,2',
    y2020: '2430,4',
    y2021: '2503,5'
  },
  {
    id: 9,
    number: 9,
    name_indicators: 'Собственные нужды электрическая энергия',
    unit: 'млн. кВтч',
    y2017: '272,1',
    y2018: '285,3',
    y2019: '323,4',
    y2020: '326,7',
    y2021: '324,8'
  },
  {
    id: 10,
    number: 9.1,
    name_indicators: 'Собственные нужды электрическая энергия',
    unit: '%',
    y2017: '15,5',
    y2018: '15,8',
    y2019: '14,7',
    y2020: '14,5',
    y2021: '15,0'
  },
  {
    id: 11,
    number: 10,
    name_indicators: 'Собственные нужды тепловая энергия',
    unit: 'тыс. Гкал',
    y2017: '106,1',
    y2018: '121,8',
    y2019: '119,9',
    y2020: '121,0',
    y2021: '121,7'
  },
  {
    id: 12,
    number: 10.1,
    name_indicators: 'Собственные нужды тепловая энергия',
    unit: '%',
    y2017: '4,1',
    y2018: '4,5',
    y2019: '4,6',
    y2020: '4,7',
    y2021: '4,6'
  },
  {
    id: 13,
    number: 11,
    name_indicators: 'Коэффициент использования установленной электрической мощности',
    unit: '%',
    y2017: '53,7',
    y2018: '55,2',
    y2019: '67,2',
    y2020: '68,7',
    y2021: '66,4'
  },
  {
    id: 14,
    number: 12,
    name_indicators: 'Коэффициент использования установленной теплововй мощности',
    unit: '%',
    y2017: '33,1',
    y2018: '35,2',
    y2019: '34,6',
    y2020: '33,8',
    y2021: '34,9'
  },
  {
    id: 15,
    number: 13,
    name_indicators: 'Удельный расход топлива на электрическую энергию',
    unit: 'гут/кВтч',
    y2017: '290,1',
    y2018: '299,6',
    y2019: '313,2',
    y2020: '320,1',
    y2021: '312,6'
  },
  {
    id: 16,
    number: 13.1,
    name_indicators: 'Удельный расход топлива на электрическую энергию',
    unit: 'г.н.т./кВтч',
    y2017: '-',
    y2018: '-',
    y2019: '-',
    y2020: '-',
    y2021: '-'
  },
  {
    id: 17,
    number: 14,
    name_indicators: 'Удельный расход топлива на тепловую энергию',
    unit: 'кгут/Гкал',
    y2017: '185,1',
    y2018: '184,5',
    y2019: '184,0',
    y2020: '184,4',
    y2021: '181,7'
  },
  {
    id: 18,
    number: 14.1,
    name_indicators: 'Удельный расход топлива на тепловую энергию',
    unit: 'кг.н.т./Гкал',
    y2017: '-',
    y2018: '-',
    y2019: '-',
    y2020: '-',
    y2021: '-'
  },
  {
    id: 19,
    number: 15,
    name_indicators: 'Общий КПД электростанции',
    unit: '%',
    y2017: '60,2',
    y2018: '59,6',
    y2019: '56,0',
    y2020: '54,9',
    y2021: '56,7'
  },
  {
    id: 20,
    number: 16,
    name_indicators: 'Износ электростанции*',
    unit: '%',
    y2017: '74,1',
    y2018: '58,1',
    y2019: '60,6',
    y2020: '63,0',
    y2021: '64,9'
  }
])

const passportData = reactive([
  {
    id: 1,
    number: 1,
    name: 'Полное наименование ЭПО',
    description: 'Товарищество с ограниченной ответственностью «Усть-Каменогорская ТЭЦ»'
  },
  {
    id: 2,
    number: 2,
    name: 'Адрес предприятия (фактический)',
    description: 'РК, ВКО, г. Усть-Каменогорск, ул. Промышленная, 2'
  },
  {
    id: 3,
    number: 3,
    name: 'Адрес предприятия (юридический)',
    description: 'РК, ВКО, г. Усть-Каменогорск, ул. Промышленная, 2'
  },
  {
    id: 4,
    number: 4,
    name: 'Местонахождение',
    description: 'РК, ВКО, г. Усть-Каменогорск, ул. Промышленная, 2'
  },
  {
    id: 5,
    number: 5,
    name: 'Геолокация по google карте (координаты)',
    description: 'Широта 49.982781849999995 / Долгота 82.61372686558872'
  },
  {
    id: 6,
    number: 6,
    name: 'БИН',
    description: '030540000538'
  },
  {
    id: 7,
    number: 7,
    name: 'Дата первичной регистрации',
    description: '06 мая 2003 г.'
  },
  {
    id: 8,
    number: 8,
    name: 'Первый руководитель (ФИО полностью): контактные данные (сотовый, городской)',
    description:
      'Генеральный директор – Бексолтан Айдын Ордабекұлы, мобильный +7-701-533-33-75, городской: 8 (7232) 290-359'
  },
  {
    id: 9,
    number: 9,
    name: 'Главный инженер (ФИО полностью): контактные данные (сотовый, городской)',
    description:
      'Директор по эксплуатации – главный инженер Ахметжанов Нурлан Габдулович, мобильный: +7-701-513-02-82, городской: 8 (7232) 290-280'
  },
  {
    id: 10,
    number: 10,
    name: 'Форма собственности',
    description: 'Частная'
  },
  {
    id: 11,
    number: 11,
    name: 'Учредители и доли участия',
    description: 'ТОО «Шыгыс Energo («Шыгыс Энерго»)», 100 % доля участия'
  },
  {
    id: 12,
    number: 12,
    name: 'Телефон приемной, канцелярии и электронная почта',
    description: 'Приемная: 8/7232/290-359'
  },
  {
    id: 13,
    number: 13,
    name: 'Климатические условия',
    description: 'Климат резко-континентальный'
  }
])

const thermalEnergyTariff = reactive([
  {
    id: 1,
    number: 1,
    name_indicators: 'Тариф ',
    unit: {
      name_1: 'тенге/кВтч'
    },
    y2017: {
      number_1: '7,50'
    },
    y2018: {
      number_1: '7,50'
    },
    y2019: {
      number_1: '5,69/6,44'
    },
    y2020: {
      number_1: '6,44/7,72'
    },
    y2021: {
      number_1: '7,72/9,68/8,48'
    },
    y2022: {
      number_1: '8,48'
    }
  },
  {
    id: 2,
    number: 2,
    name_indicators: 'Себестоимость',
    unit: {
      name_1: 'тенге/кВтч'
    },
    y2017: {
      number_1: '5,73'
    },
    y2018: {
      number_1: '5,72'
    },
    y2019: {
      number_1: '5,92'
    },
    y2020: {
      number_1: '6,39'
    },
    y2021: {
      number_1: '6,91'
    },
    y2022: {
      number_1: '8,70'
    }
  },
  {
    id: 3,
    number: 3,
    name_indicators: 'Топливная составляющая (уголь, мазут), в т.ч.',
    unit: {
      name_1: 'тенге/кВтч'
    },
    y2017: {
      number_1: '2,00'
    },
    y2018: {
      number_1: '2,34'
    },
    y2019: {
      number_1: '2,50'
    },
    y2020: {
      number_1: '2,60'
    },
    y2021: {
      number_1: '2,80'
    },
    y2022: {
      number_1: '3,52'
    }
  },
  {
    id: 4,
    number: 3.1,
    name_indicators: 'Стоимость топлива (уголь Каражыра)',
    unit: {
      name_1: 'тенге/тонна'
    },
    y2017: {
      number_1: '2848,21'
    },
    y2018: {
      number_1: '2991,07'
    },
    y2019: {
      number_1: '3141,07'
    },
    y2020: {
      number_1: '3298,21'
    },
    y2021: {
      number_1: '3582,52'
    },
    y2022: {
      number_1: '3833,04'
    }
  },
  {
    id: 5,
    number: 3.2,
    name_indicators: 'Объем топлива (уголь Каражыра)',
    unit: {
      name_1: 'тонн'
    },
    y2017: {
      number_1: '491799'
    },
    y2018: {
      number_1: '503760'
    },
    y2019: {
      number_1: '713542'
    },
    y2020: {
      number_1: '857351'
    },
    y2021: {
      number_1: '862667'
    },
    y2022: {
      number_1: '867166'
    }
  },
  {
    id: 6,
    number: 3.3,
    name_indicators: 'Цена транспортировки (уголь Каражыра)',
    unit: {
      name_1: 'тенге/тонна',
      name_2: 'тенге/кВтч'
    },
    y2017: {
      number_1: '1711,12',
      number_2: '0,0012'
    },
    y2018: {
      number_1: '2101,90',
      number_2: '0,0014'
    },
    y2019: {
      number_1: '2192,71',
      number_2: '0,0012'
    },
    y2020: {
      number_1: '2307,96',
      number_2: '0,0012'
    },
    y2021: {
      number_1: '2402,16',
      number_2: '0,0013'
    },
    y2022: {
      number_1: '2865,85',
      number_2: '0,0016'
    }
  },
  {
    id: 7,
    number: 3.4,
    name_indicators: 'Стоимость топлива (уголь Майкуба)',
    unit: {
      name_1: 'тенге/тонна'
    },
    y2017: {
      number_1: '2533,44'
    },
    y2018: {
      number_1: '2638,39'
    },
    y2019: {
      number_1: '2638,39'
    },
    y2020: {
      number_1: '2902,00'
    },
    y2021: {
      number_1: '-'
    },
    y2022: {
      number_1: '-'
    }
  },
  {
    id: 8,
    number: 3.5,
    name_indicators: 'Объем топлива (уголь Майкуба)',
    unit: {
      name_1: 'тонн'
    },
    y2017: {
      number_1: '150953'
    },
    y2018: {
      number_1: '187893'
    },
    y2019: {
      number_1: '156768'
    },
    y2020: {
      number_1: '41202'
    },
    y2021: {
      number_1: '-'
    },
    y2022: {
      number_1: '-'
    }
  },
  {
    id: 9,
    number: 3.6,
    name_indicators: 'Цена транспортировки (уголь Майкуба)',
    unit: {
      name_1: 'тенге/тонна',
      name_2: 'тенге/кВтч'
    },
    y2017: {
      number_1: '1962,78',
      number_2: '0,0013'
    },
    y2018: {
      number_1: '2439,29',
      number_2: '0,0016'
    },
    y2019: {
      number_1: '2639,89',
      number_2: '0,0014'
    },
    y2020: {
      number_1: '2352,37',
      number_2: '0,0012'
    },
    y2021: {
      number_1: '-',
      number_2: '0,0000'
    },
    y2022: {
      number_1: '-',
      number_2: '0,0000'
    }
  },
  {
    id: 10,
    number: 3.7,
    name_indicators: 'Стоимость топлива (мазут)',
    unit: {
      name_1: 'тенге/тонна'
    },
    y2017: {
      number_1: '36108,94'
    },
    y2018: {
      number_1: '43698,71'
    },
    y2019: {
      number_1: '61521,83'
    },
    y2020: {
      number_1: '78436,35'
    },
    y2021: {
      number_1: '70736,96'
    },
    y2022: {
      number_1: '79919,80'
    }
  },
  {
    id: 11,
    number: 3.8,
    name_indicators: 'Объем топлива (мазут)',
    unit: {
      name_1: 'тонн'
    },
    y2017: {
      number_1: '760'
    },
    y2018: {
      number_1: '535'
    },
    y2019: {
      number_1: '890'
    },
    y2020: {
      number_1: '534'
    },
    y2021: {
      number_1: '603'
    },
    y2022: {
      number_1: '894'
    }
  },
  {
    id: 11,
    number: 4,
    name_indicators: 'Амортизация',
    unit: {
      name_1: 'тенге/кВтч'
    },
    y2017: {
      number_1: '0,61'
    },
    y2018: {
      number_1: '0,62'
    },
    y2019: {
      number_1: '0,59'
    },
    y2020: {
      number_1: '0,69'
    },
    y2021: {
      number_1: '0,98'
    },
    y2022: {
      number_1: '1,10'
    }
  },
  {
    id: 12,
    number: 5,
    name_indicators:
      'Ремонты, не приводящие к увеличению стоимости (с учетом материалов на ремонт)',
    unit: {
      name_1: 'тенге/кВтч'
    },
    y2017: {
      number_1: '0,25'
    },
    y2018: {
      number_1: '0,37'
    },
    y2019: {
      number_1: '0,72'
    },
    y2020: {
      number_1: '0,20'
    },
    y2021: {
      number_1: '0,35'
    },
    y2022: {
      number_1: '1,06'
    }
  },
  {
    id: 13,
    number: 6,
    name_indicators: 'Инвестиционная программа (с учетом возврата основного долга по займам)',
    unit: {
      name_1: 'тыс. тенге'
    },
    y2017: {
      number_1: '3407122'
    },
    y2018: {
      number_1: '3010530'
    },
    y2019: {
      number_1: '1212190'
    },
    y2020: {
      number_1: '993166'
    },
    y2021: {
      number_1: '1833819'
    },
    y2022: {
      number_1: '1356209'
    }
  },
  {
    id: 14,
    number: 7,
    name_indicators: 'Фонд оплаты труда',
    unit: {
      name_1: 'тыс. тенге'
    },
    y2017: {
      number_1: '833784'
    },
    y2018: {
      number_1: '758657'
    },
    y2019: {
      number_1: '784699'
    },
    y2020: {
      number_1: '1017346'
    },
    y2021: {
      number_1: '1331517'
    },
    y2022: {
      number_1: '2148932'
    }
  },
  {
    id: 15,
    number: 8,
    name_indicators: 'Объем реализации',
    unit: {
      name_1: 'тыс. кВтч'
    },
    y2017: {
      number_1: '1474454'
    },
    y2018: {
      number_1: '1512108'
    },
    y2019: {
      number_1: '1876147'
    },
    y2020: {
      number_1: '1951608'
    },
    y2021: {
      number_1: '1862117'
    },
    y2022: {
      number_1: '1823306'
    }
  },
  {
    id: 16,
    number: 9,
    name_indicators: 'Средневзвешанный тариф реализации',
    unit: {
      name_1: 'тыс. кВтч'
    },
    y2017: {
      number_1: '7,50'
    },
    y2018: {
      number_1: '7,50'
    },
    y2019: {
      number_1: '5,91'
    },
    y2020: {
      number_1: '7,09'
    },
    y2021: {
      number_1: '8,51'
    },
    y2022: {
      number_1: '8,48'
    }
  }
])

const teps = reactive([
  {
    id: 1,
    field: 'number',
    header: '№'
  },
  {
    id: 2,
    field: 'name_indicators',
    header: 'Наименование показателей'
  },
  {
    id: 3,
    field: 'unit',
    header: 'Ед. изм.'
  },
  {
    id: 4,
    field: 'y2017',
    header: '2017'
  },
  {
    id: 5,
    field: 'y2018',
    header: '2018'
  },
  {
    id: 6,
    field: 'y2019',
    header: '2019'
  },
  {
    id: 7,
    field: 'y2020',
    header: '2020'
  },
  {
    id: 8,
    field: 'y2021',
    header: '2021'
  }
])

onMounted(() => {
  chartData.value = verticalBar(chart)
  chartData2.value = doughnut(chart)
  chartData3.value = verticalBar(chart2)
  chartData4.value = doughnut(chart2)
  chartOptions.value = setChartOptions()
})

const chartData = ref()
const chartData2 = ref()
const chartData3 = ref()
const chartData4 = ref()
const chartOptions = ref()

let chart = reactive({
  labels: [2019, 2020, 2021, 2022],
  data: [
    {
      label: 'План (млн. тенге)',
      color: 'blue',
      data: [1212190, 993166, 1833819, 1356209]
    },
    {
      label: 'Факт (млн. тенге)',
      color: 'yellow',
      data: [1212190, 993166, 1833819, 1356209]
    }
  ],
  data2: [49, 76, 64, 0]
})

let chart2 = reactive({
  labels: [2019, 2020, 2021, 2022],
  data: [
    {
      label: 'План (млн. тенге)',
      color: 'blue',
      data: [1414303, 774162, 1059965, 1700589]
    },
    {
      label: 'Факт (млн. тенге)',
      color: 'yellow',
      data: [1416578, 779191, 1064561, 0]
    }
  ],
  data2: [26, 7, 5, 0]
})
</script>

<template>
  <div class="container">
    <div class="card mb-3">
      <TabMenu class="border-round-lg" :model="items" />
    </div>

    <div class="card flex bg-white border-round-lg">
      <div>
        <img src="./assets/images/1.png" alt="" />
      </div>
      <div>
        <h1>АО “Астана-Энергия” ТЭЦ-2</h1>
        <p>Бин: 041140002811</p>
        <p>Ссылка: https://astana-energy.kz/</p>
        <p>Дата последнего изменения данных: 20.08.2022 13:23:00</p>
        <Button label="Скачать PDF" icon="pi pi-file-pdf" />
      </div>
    </div>

    <!-- ТЭП -->
    <h1>Технико-экономические показатели</h1>
    <div class="card border-round-lg p-4 bg-white">
      <DataTable showGridlines :value="technicalEconomicIndicators">
        <Column v-for="tep in teps" :key="tep.id" :field="tep.field" :header="tep.header" />
      </DataTable>
    </div>
    <!-- ТЭП -->

    <!-- Краткая справка -->
    <h1>Краткая справка</h1>
    <div class="card border-round-lg p-4 bg-white">
      <p>
        <span class="font-bold">Усть-Каменогорская ТЭЦ</span> — ТОО «Усть-Каменогорская ТЭЦ» -
        теплоэлектроцентраль, расположенная в городе Усть-Каменогорске Восточно-Казахстанской
        области, Казахстан. Принадлежит ТОО «Шыгыс Energo («Шыгыс Энерго»)» (находится в частной
        собственности). Площадка ТОО «Усть-Каменогорская ТЭЦ» расположена в черте города в пределах
        второй надпойменной террасы р. Ульба. Занимаемая площадь 42 га. Установленная мощность ТОО
        «Усть-Каменогорская ТЭЦ» по состоянию на 01.01.2022г. года составляет: <br />
        - электрическая - 372,5 МВт <br />
        - тепловая – 859,9 Гкал/ч.
      </p>
    </div>
    <!-- Краткая справка -->

    <!-- Паспортные данные -->
    <h1>Паспортные данные</h1>
    <div class="card border-round-lg p-4 bg-white">
      <DataTable showGridlines :value="passportData">
        <Column field="number" header="№"></Column>
        <Column field="name" header="Наименование"></Column>
        <Column field="description" header="Описание"></Column>
      </DataTable>
    </div>
    <!-- Паспортные данные -->

    <!-- Тарифы -->
    <h1>Тарифы</h1>
    <div class="card border-round-lg p-4 bg-white">
      <!-- <h3>По производству электрической энергии</h3> -->
      <DataTable showGridlines :value="thermalEnergyTariff">
        <Column field="number" header="№"></Column>
        <Column field="name_indicators" header="Наименование показателей"></Column>
        <Column field="unit" header="Ед. изм.">
          <template #body="slotProps">
            <div>
              {{ slotProps.data.unit.name_1 }}
            </div>
            <div>
              {{ slotProps.data.unit.name_2 }}
            </div>
          </template>
        </Column>

        <Column field="y2017" header="2017">
          <template #body="slotProps">
            <div>
              {{ slotProps.data.y2017.number_1 }}
            </div>
            <div>
              {{ slotProps.data.y2017.number_2 }}
            </div>
          </template>
        </Column>

        <Column field="y2018" header="2018">
          <template #body="slotProps">
            <div>
              {{ slotProps.data.y2018.number_1 }}
            </div>
            <div>
              {{ slotProps.data.y2018.number_2 }}
            </div>
          </template>
        </Column>

        <Column field="y2019" header="2019">
          <template #body="slotProps">
            <div>
              {{ slotProps.data.y2019.number_1 }}
            </div>
            <div>
              {{ slotProps.data.y2019.number_2 }}
            </div>
          </template>
        </Column>

        <Column field="y2020" header="2020">
          <template #body="slotProps">
            <div>
              {{ slotProps.data.y2020.number_1 }}
            </div>
            <div>
              {{ slotProps.data.y2020.number_2 }}
            </div>
          </template>
        </Column>

        <Column field="y2021" header="2021">
          <template #body="slotProps">
            <div>
              {{ slotProps.data.y2021.number_1 }}
            </div>
            <div>
              {{ slotProps.data.y2021.number_2 }}
            </div>
          </template>
        </Column>

        <Column field="y2022" header="2022">
          <template #body="slotProps">
            <div>
              {{ slotProps.data.y2022.number_1 }}
            </div>
            <div>
              {{ slotProps.data.y2022.number_2 }}
            </div>
          </template>
        </Column>
      </DataTable>
    </div>
    <!-- Тарифы -->

    <!-- Инвестиционная программа -->
    <div class="card flex justify-content-between border-round-lg p-4 bg-white">
      <Chart type="bar" :data="chartData" :options="chartOptions" class="w-full h-30rem" />
      <Chart type="doughnut" :data="chartData2" :options="chartOptions" class="w-full md:w-30rem" />
    </div>

    <div class="card flex justify-content-between border-round-lg p-4 bg-white">
      <Chart type="bar" :data="chartData3" :options="chartOptions" class="w-full h-30rem" />
      <Chart type="doughnut" :data="chartData4" :options="chartOptions" class="w-full md:w-30rem" />
    </div>
    <!-- Инвестиционная программа -->

    <router-view />
  </div>
</template>

<style scoped></style>
