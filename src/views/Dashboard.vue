<template lang="pug">
v-container(fill-height fluid grid-list-xl)
    v-layout(wrap)
        v-flex(md12 sm12 lg4)
            material-chart-card(:data='dailySalesChart.data', :options='dailySalesChart.options', color='red', type='Line')
                h4.title.font-weight-light Filmes assistidos
                //- colocar último filme asssistido
                p.category.d-inline-flex.font-weight-light Preencher

        v-flex(md12='', sm12='', lg4='')
            material-chart-card(:data='dataCompletedTasksChart.data', :options='dataCompletedTasksChart.options', color='green', type='Bar')
                h3.title.font-weight-light Categorias mais assistidas
                //- colocar última categoria assistida
                p.category.d-inline-flex.font-weight-light Preencher

        v-flex(sm6='', xs12='', md6='', lg3='')
            material-stats-card(color='green', icon='mdi-store', title='Revenue', value='$34,245', sub-icon='mdi-calendar', sub-text='Last 24 Hours')
        v-flex(sm6='', xs12='', md6='', lg3='')
            material-stats-card(color='orange', icon='mdi-content-copy', title='Used Space', value='49/50', small-value='GB', sub-icon='mdi-alert', sub-icon-color='error', sub-text='Get More Space...', sub-text-color='text-primary')
        v-flex(sm6='', xs12='', md6='', lg3='')
            material-stats-card(color='red', icon='mdi-information-outline', title='Fixed Issues', value='75', sub-icon='mdi-tag', sub-text='Tracked from Github')
        v-flex(sm6='', xs12='', md6='', lg3='')
            material-stats-card(color='info', icon='mdi-twitter', title='Followers', value='+245', sub-icon='mdi-update', sub-text='Just Updated')
        v-flex(md12='', lg6='')
            material-card(color='orange', title='Employee Stats', text='New employees on 15th September, 2016')
                v-data-table(:headers='headers', :items='items', hide-actions='')
                    template(slot='headerCell', slot-scope='{ header }')
                        span.font-weight-light.text-warning.text--darken-3(v-text='header.text')
                    template(slot='items', slot-scope='{ index, item }')
                        | {{ index + 1 }}
                        | {{ item.name }}
                        | {{ item.salary }}
                        | {{ item.country }}
                        | {{ item.city }}
        v-flex(md12='', lg6='')
            material-card.card-tabs(color='green')
                v-flex(slot='header')
                    v-tabs(v-model='tabs', color='transparent', slider-color='white')
                        span.subheading.font-weight-light.mr-3(style='align-self: center;') Tasks:
                        v-tab.mr-3
                            v-icon.mr-2 mdi-bug
                            |  Bugs
                        v-tab.mr-3
                            v-icon.mr-2 mdi-code-tags
                            |  Website
                        v-tab
                            v-icon.mr-2 mdi-cloud
                            |  Server
                v-tabs-items(v-model='tabs')
                    v-tab-item(v-for='n in 3', :key='n')
                        v-list(three-line='')
                            v-list-tile(@click='complete(0)')
                                v-list-tile-action
                                    v-checkbox(:value='list[0]', color='green')
                                v-list-tile-title Sign contract for "What are conference organized afraid of?"
                                .d-flex
                                    v-tooltip(top='', content-class='top')
                                        v-btn.v-btn--simple(slot='activator', color='success', icon='')
                                            v-icon(color='primary') mdi-pencil
                                        span Edit
                                    v-tooltip(top='', content-class='top')
                                        v-btn.v-btn--simple(slot='activator', color='danger', icon='')
                                            v-icon(color='error') mdi-close
                                        span Close
                            v-divider
                                v-list-tile(@click='complete(1)')
                                    v-list-tile-action
                                        v-checkbox(:value='list[1]', color='success')
                                    v-list-tile-title Lines From Great Russian Literature? Or E-mails From My Boss?
                                    .d-flex
                                        v-tooltip(top='', content-class='top')
                                            v-btn.v-btn--simple(slot='activator', color='success', icon='')
                                                v-icon(color='primary') mdi-pencil
                                            span Edit
                                        v-tooltip(top='', content-class='top')
                                            v-btn.v-btn--simple(slot='activator', color='danger', icon='')
                                                v-icon(color='error') mdi-close
                                            span Close
                                v-divider
                                    v-list-tile(@click='complete(2)')
                                        v-list-tile-action
                                            v-checkbox(:value='list[2]', color='success')
                                        v-list-tile-title
                                            | Flooded: One year later, assessing what was lost and what was found when a ravaging rain swept through metro Detroit
                                        .d-flex
                                            v-tooltip(top='', content-class='top')
                                                v-btn.v-btn--simple(slot='activator', color='success', icon='')
                                                    v-icon(color='primary') mdi-pencil
                                                span Edit
                                            v-tooltip(top='', content-class='top')
                                                v-btn.v-btn--simple(slot='activator', color='danger', icon='')
                                                    v-icon(color='error') mdi-close
                                                span Close
</template>
<script>
export default {
  data () {
    return {
      dailySalesChart: {
        data: {
          labels: ['M', 'T', 'W', 'T', 'F', 'S', 'S'],
          series: [
            [200, 217, 227, 217, 223, 218, 238]
          ]
        },
        options: {
          lineSmooth: this.$chartist.Interpolation.cardinal({
            tension: 0
          }),
          low: 0,
          high: 500, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
          chartPadding: {
            top: 0,
            right: 0,
            bottom: 0,
            left: 0
          }
        }
      },
      dataCompletedTasksChart: {
        data: {
          labels: ['Drama', '3pm', '6pm', '9pm', '12pm', '3am', '6am', '9am', '5612'],
          series: [
            [230, 750, 450, 300, 280, 240, 200, 190, 500]
          ]
        },
        options: {
          lineSmooth: this.$chartist.Interpolation.cardinal({
            tension: 0
          }),
          low: 0,
          high: 800, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
          chartPadding: {
            top: 0,
            right: 0,
            bottom: 0,
            left: 0
          }
        }
      },
      headers: [
        {
          sortable: false,
          text: 'ID',
          value: 'id'
        },
        {
          sortable: false,
          text: 'Name',
          value: 'name'
        },
        {
          sortable: false,
          text: 'Salary',
          value: 'salary',
          align: 'right'
        },
        {
          sortable: false,
          text: 'Country',
          value: 'country',
          align: 'right'
        },
        {
          sortable: false,
          text: 'City',
          value: 'city',
          align: 'right'
        }
      ],
      items: [
        {
          name: 'Dakota Rice',
          country: 'Niger',
          city: 'Oud-Tunrhout',
          salary: '$35,738'
        },
        {
          name: 'Minerva Hooper',
          country: 'Curaçao',
          city: 'Sinaai-Waas',
          salary: '$23,738'
        }, {
          name: 'Sage Rodriguez',
          country: 'Netherlands',
          city: 'Overland Park',
          salary: '$56,142'
        }, {
          name: 'Philip Chanley',
          country: 'Korea, South',
          city: 'Gloucester',
          salary: '$38,735'
        }, {
          name: 'Doris Greene',
          country: 'Malawi',
          city: 'Feldkirchen in Kārnten',
          salary: '$63,542'
        }
      ],
      tabs: 0,
      list: {
        0: false,
        1: false,
        2: false
      }
    }
  },
  methods: {
    complete (index) {
      this.list[index] = !this.list[index]
    }
  }
}
</script>
