<template>
  <div>
    <!-- WIDGET CONFIGURATOR -->
    <div class="row">
      <card>
        <div slot="header">
          <h4 class="card-title">Widgets</h4>
        </div>

        <div class="row">
          <!-- WIDGET SELECTOR AND FORMS -->
          <div class="col-6">
            <!-- WIDGETS SELECTOR -->
            <el-select
              v-model="widgetType"
              class="select-success"
              placeholder="Selecciona un Widget"
              style="width: 100%;"
            >
              <el-option
                class="text-dark"
                value="numberchart"
                label="Representación Gráfica"
              >
              </el-option>
              <el-option
                class="text-dark"
                value="indicator"
                label="Indicator Booleano"
              >
              </el-option>
              <el-option
                class="text-dark"
                value="map"
                label="Mapa"
              ></el-option>
              <el-option
                class="text-dark"
                value="switch"
                label="Switch"
              ></el-option>
              <el-option
                class="text-dark"
                value="button"
                label="Botón"
              ></el-option>
            </el-select>

            <br />
            <br />

            <!-- FORMS NUMBER CHART TYPE -->
            <div v-if="widgetType == 'numberchart'">
              <base-input
                v-model="ncConfig.variableFullName"
                label="Nombre Var"
                type="text"
              >
              </base-input>

              <base-input v-model="ncConfig.unit" label="Unit" type="text">
              </base-input>
              <base-input
                v-model.number="ncConfig.decimalPlaces"
                label="Decimal"
                type="number"
              >
              </base-input>

              <label>Iconos</label>
              <el-select
                v-model="ncConfig.icon"               
                placeholder="Iconos"
                class="select-success"
                style="width: 100%;"
              >
                <el-option      
                  class="text-dark"                             
                  value="tim-icons icon-alert-circle-exc"
                  label="Alarma "
                  
                ></el-option>
                
                <el-option   
                  class="text-dark"          
                  value="tim-icons icon-app"
                  label="Cubo"  
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-atom"
                  label="Átomo"
                ></el-option>   

                <el-option  
                  class="text-dark"             
                  value="fa-sun"
                  label="Sol"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bank"
                  label="Banco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bulb-63"
                  label="Foco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-button-power"
                  label="Power"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-bar-32"
                  label="Gráfico de Barras"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-pie-36"
                  label="Gráfico de pastel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-cloud-upload-94"
                  label="Nube"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-image-02"
                  label="Paisaje"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-molecule-40"
                  label="Molécula"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-send"
                  label="Avión Papel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-sound-wave"
                  label="Ondas"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-world"
                  label="Mundo"
                ></el-option>

                
              </el-select>

              <base-input
                v-model.number="ncConfig.variableSendFreq"
                label="Frec. Envío"
                type="number"
              ></base-input>

              <base-input
                v-model.number="ncConfig.chartTimeAgo"
                label="Presentación del Tiempo (mins)"
                type="number"
              ></base-input>
              <label>Color</label>
              <el-select
                v-model="ncConfig.class"
                class="select-success"
                placeholder="Color"
                style="width: 100%;"
              >
                <el-option
                  class="text-success"
                  value="success"
                  label="Verde"
                ></el-option>
                <el-option
                  class="text-primary"
                  value="primary"
                  label="Violeta"
                ></el-option>
                <el-option
                  class="text-warning"
                  value="warning"
                  label="Naranja"
                ></el-option>
                <el-option
                  class="text-danger"
                  value="danger"
                  label="Rojo"
                ></el-option>
              </el-select>
              <br>
              <label>Tamaño de Columna</label>
              <el-select
                v-model="ncConfig.column"
                class="select-success"
                placeholder="Tamaño de Columna"
                style="width: 100%;"
              >
                <el-option
                  class="text-dark"
                  value="col-3"
                  label="Cuarto"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-6"
                  label="Mitad"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-12"
                  label="Completo"
                ></el-option>
              </el-select>

              <br /><br />
            </div>

            <!-- FORM SWITCH TYPE -->
            <div v-if="widgetType == 'switch'">
              <base-input
                v-model="iotSwitchConfig.variableFullName"
                label="Nombre var"
                type="text"
              >
              </base-input>
              <label>Iconos</label>
              <el-select
                v-model="iotSwitchConfig.icon"               
                placeholder="Iconos"
                class="select-success"
                style="width: 100%;"
              >
                <el-option      
                  class="text-dark"                             
                  value="tim-icons icon-alert-circle-exc"
                  label="Alarma "
                  
                ></el-option>
                
                <el-option   
                  class="text-dark"          
                  value="tim-icons icon-app"
                  label="Cubo"  
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-atom"
                  label="Átomo"
                ></el-option>   

                <el-option  
                  class="text-dark"             
                  value="fa-sun"
                  label="Sol"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bank"
                  label="Banco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bulb-63"
                  label="Foco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-button-power"
                  label="Power"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-bar-32"
                  label="Gráfico de Barras"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-pie-36"
                  label="Gráfico de pastel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-cloud-upload-94"
                  label="Nube"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-image-02"
                  label="Paisaje"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-molecule-40"
                  label="Molécula"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-send"
                  label="Avión Papel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-sound-wave"
                  label="Ondas"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-world"
                  label="Mundo"
                ></el-option>

                
              </el-select>
              <label>Color</label>
              <el-select
                v-model="iotSwitchConfig.class"
                class="select-success"
                placeholder="Color"
                style="width: 100%;"
              >
                <el-option
                  class="text-success"
                  value="success"
                  label="Verde"
                ></el-option>
                <el-option
                  class="text-primary"
                  value="primary"
                  label="Violeta"
                ></el-option>
                <el-option
                  class="text-warning"
                  value="warning"
                  label="Naranja"
                ></el-option>
                <el-option
                  class="text-danger"
                  value="danger"
                  label="Rojo"
                ></el-option>
              </el-select>
              
              <label>Tamaño de Columna</label>
              <el-select
                v-model="iotSwitchConfig.column"
                class="select-success"
                placeholder="Tamaño de Columna"
                style="width: 100%;"
              >
                <el-option
                  class="text-dark"
                  value="col-3"
                  label="Cuarto"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-6"
                  label="Mitad"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-12"
                  label="Completo"
                ></el-option>
              </el-select>



              <br /><br />
            </div>

            <!-- FORM BUTTON TYPE -->
            <div v-if="widgetType == 'button'">
              <base-input
                v-model="configButton.variableFullName"
                label="Nombre Var"
                type="text"
              >
              </base-input>

              <base-input
                v-model="configButton.message"
                label="Mensaje"
                type="text"
              >
              </base-input>

              <base-input
                v-model="configButton.text"
                label="Texto Botón"
                type="text"
              >
              </base-input>

              <label>Iconos</label>
              <el-select
                v-model="configButton.icon"               
                placeholder="Iconos"
                class="select-success"
                style="width: 100%;"
              >
                <el-option      
                  class="text-dark"                             
                  value="tim-icons icon-alert-circle-exc"
                  label="Alarma "
                  
                ></el-option>
                
                <el-option   
                  class="text-dark"          
                  value="tim-icons icon-app"
                  label="Cubo"  
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-atom"
                  label="Átomo"
                ></el-option>   

                <el-option  
                  class="text-dark"             
                  value="fa-sun"
                  label="Sol"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bank"
                  label="Banco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bulb-63"
                  label="Foco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-button-power"
                  label="Power"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-bar-32"
                  label="Gráfico de Barras"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-pie-36"
                  label="Gráfico de pastel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-cloud-upload-94"
                  label="Nube"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-image-02"
                  label="Paisaje"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-molecule-40"
                  label="Molécula"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-send"
                  label="Avión Papel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-sound-wave"
                  label="Ondas"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-world"
                  label="Mundo"
                ></el-option>

                
              </el-select>

              <label>Color</label>
              <el-select
                v-model="configButton.class"
                class="select-success"
                placeholder="Color"
                style="width: 100%;"
              >
                <el-option
                  class="text-success"
                  value="success"
                  label="Verde"
                ></el-option>
                <el-option
                  class="text-primary"
                  value="primary"
                  label="Violeta"
                ></el-option>
                <el-option
                  class="text-warning"
                  value="warning"
                  label="Naranja"
                ></el-option>
                <el-option
                  class="text-danger"
                  value="danger"
                  label="Rojo"
                ></el-option>
              </el-select>

              <br /><br /><br />

              <label>Tamaño de Columna</label>
              <el-select
                v-model="configButton.column"
                class="select-success"
                placeholder="Tamaño de Columna"
                style="width: 100%;"
              >
                <el-option
                  class="text-dark"
                  value="col-3"
                  label="Cuarto"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-6"
                  label="Mitad"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-12"
                  label="Completo"
                ></el-option>
              </el-select>

              <br /><br />
            </div>

            <!-- FORM INDICATOR TYPE -->
            <div v-if="widgetType == 'indicator'">

              <base-input
                v-model="iotIndicatorConfig.variableFullName"
                label="Nombre Var"
                type="text"
              >
              </base-input>

              <label>Iconos</label>
              <el-select
                v-model="iotIndicatorConfig.icon"               
                placeholder="Iconos"
                class="select-success"
                style="width: 100%;"
              >
                <el-option      
                  class="text-dark"                             
                  value="tim-icons icon-alert-circle-exc"
                  label="Alarma "
                  
                ></el-option>
                
                <el-option   
                  class="text-dark"          
                  value="tim-icons icon-app"
                  label="Cubo"  
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-atom"
                  label="Átomo"
                ></el-option>   

                <el-option  
                  class="text-dark"             
                  value="fa-sun"
                  label="Sol"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bank"
                  label="Banco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-bulb-63"
                  label="Foco"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-button-power"
                  label="Power"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-bar-32"
                  label="Gráfico de Barras"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-chart-pie-36"
                  label="Gráfico de pastel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-cloud-upload-94"
                  label="Nube"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-image-02"
                  label="Paisaje"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-molecule-40"
                  label="Molécula"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-send"
                  label="Avión Papel"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-sound-wave"
                  label="Ondas"
                ></el-option>

                <el-option  
                  class="text-dark"             
                  value="tim-icons icon-world"
                  label="Mundo"
                ></el-option>

                
              </el-select>

              <br />

              <base-input
                v-model="iotIndicatorConfig.variableSendFreq"
                label="Frecuencia Envío"
                type="text"
              ></base-input>

              <br />

              <label>Color</label>
              <el-select
                v-model="iotIndicatorConfig.class"
                class="select-success"
                placeholder="Color"
                style="width: 100%;"
              >
                <el-option
                  class="text-success"
                  value="success"
                  label="Verde"
                ></el-option>
                <el-option
                  class="text-primary"
                  value="primary"
                  label="Violeta"
                ></el-option>
                <el-option
                  class="text-warning"
                  value="warning"
                  label="Naranja"
                ></el-option>
                <el-option
                  class="text-danger"
                  value="danger"
                  label="Rojo"
                ></el-option>
              </el-select>              

              <br /><br /><br />

              <label>Tamaño de Columna</label>
              <el-select
                v-model="iotIndicatorConfig.column"
                class="select-success"
                placeholder="Tamaño de Columna"
                style="width: 100%;"
              >
                <el-option
                  class="text-dark"
                  value="col-3"
                  label="Cuarto"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-6"
                  label="Mitad"
                ></el-option>
                <el-option
                  class="text-dark"
                  value="col-12"
                  label="Completo"
                ></el-option>
              </el-select>

              <br /><br />
            </div>
          </div>

          <!-- WIDGET PREVIEW -->
          <div class="col-6">
            <Rtnumberchart
              v-if="widgetType == 'numberchart'"
              :config="ncConfig"
            ></Rtnumberchart>
            <Iotswitch
              v-if="widgetType == 'switch'"
              :config="iotSwitchConfig"
            ></Iotswitch>
            <Iotbutton
              v-if="widgetType == 'button'"
              :config="configButton"
            ></Iotbutton>
            <Iotindicator
              v-if="widgetType == 'indicator'"
              :config="iotIndicatorConfig"
            ></Iotindicator>
          </div>
        </div>

        <!-- ADD WIDGET BUTTON -->
        <div class="row pull-right">
          <div class="col-12">
            <base-button
              native-type="submit"
              type="primary"
              class="mb-3"
              size="lg"
              @click="addNewWidget()"
            >
              Añadir Widget
            </base-button>
          </div>
        </div>
      </card>
    </div> 

    <!-- DASHBOARD PREVIEW -->
    <div class="row">
      <div
        v-for="(widget, index) in widgets"
        :key="index"
        :class="[widget.column]"
      >
        <i
          aria-hidden="true"
          class="fa fa-trash text-warning pull-right"
          @click="deleteWidget(index)"
          style="margin-bottom: 10px;"
        ></i>

        <Rtnumberchart
          v-if="widget.widget == 'numberchart'"
          :config="widget"
        ></Rtnumberchart>

        <Iotswitch
          v-if="widget.widget == 'switch'"
          :config="widget"
        ></Iotswitch>

        <Iotbutton
          v-if="widget.widget == 'button'"
          :config="widget"
        ></Iotbutton>

        <Iotindicator
          v-if="widget.widget == 'indicator'"
          :config="widget"
        ></Iotindicator>
      </div>
    </div>

    <!-- SAVE TEMPLATE FORM-->
    <div class="row" >
      <card>
        <div slot="header">
          <h4 class="card-title">Guardar Plantilla</h4>
        </div>

        <div class="row">
          <base-input
            class="col-4"
            v-model="templateName"
            label="Nombre Plantilla"
            type="text"
          >
          </base-input>

          <base-input
            class="col-8"
            v-model="templateDescription"
            label="Descripción Plantilla"
            type="text"
          >
          </base-input>
        </div>

        <br /><br />

        <div class="row">
          <div class="col-12">
            <base-button
              native-type="submit"
              type="primary"
              class="mb-3 pull-right"
              size="lg"
              @click="saveTemplate()"
              :disabled="widgets.length == 0"
            >
              Guardar Plantilla
            </base-button>
          </div>
        </div>
      </card>
    </div>

    <!-- TEMPLATES TABLE -->
    <div class="row">
      <card>
        <div slot="header">
          <h4 class="card-title">Plantillas</h4>
        </div>

        <div class="row">
          <el-table :data="templates">
            <el-table-column min-width="50" label="#" align="center">
              <div class="photo" slot-scope="{ $index }">
                {{ $index + 1 }}
              </div>
            </el-table-column>

            <el-table-column prop="name" label="Nombre"></el-table-column>

            <el-table-column
              prop="description"
              label="Descripción"
            ></el-table-column>

            <el-table-column
              prop="widgets.length"
              label="Widgets"
            ></el-table-column>

            <el-table-column header-align="right" align="right" label="Acciones">
              <div
                slot-scope="{ row }"
                class="text-right table-actions"
              >
                <el-tooltip
                  content="Delete"
                  effect="light"
                  :open-delay="300"
                  placement="top"
                >
                  <base-button
                    @click="deleteTemplate(row)"
                    type="danger"
                    icon
                    size="sm"
                    class="btn-link"
                  >
                    <i class="tim-icons icon-simple-remove "></i>
                  </base-button>
                </el-tooltip>
              </div>
            </el-table-column>
          </el-table>
        </div>
      </card>
    </div>


  </div>
</template>

<script>
import { Table, TableColumn } from "element-ui";
import { Select, Option } from "element-ui";

export default {
  middleware: "authenticated",
  components: {
    [Table.name]: Table,
    [TableColumn.name]: TableColumn,
    [Option.name]: Option,
    [Select.name]: Select
  },
  data() {
    return {
      widgets: [],
      templates: [],
      widgetType: "",
      templateName: "",
      templateDescription: "",


      ncConfig: {
        userId: "sampleuserid",
        selectedDevice: {
          name: "Disp. Nombre",
          dId: "8888"
        },
        variableFullName: "Variable",
        variable: "varname",
        variableType: "input",
        variableSendFreq: "30",
        unit: "(Unidades)",
        class: "success",
        column: "",
        decimalPlaces: 2,
        widget: "numberchart",
        icon: "",
        chartTimeAgo: 60,
        demo: true
      },

      iotSwitchConfig: {
        userId: "userid",
        selectedDevice: {
          name: "Home",
          dId: "8888"
        },
        variableFullName: "Luz",
        variable: "varname",
        variableType: "output",
        class: "danger",
        widget: "switch",
        icon: "fa-bath",
        column: "col-6"
      },


      iotIndicatorConfig: {
        userId: "userid",
        selectedDevice: {
          name: "Home",
          dId: "8888"
        },
        variableFullName: "temperature",
        variable: "varname",
        variableType: "input",
        variableSendFreq: "30",
        class: "success",
        widget: "indicator",
        icon: "fa-bath",
        column: "col-6"
      },

      configButton: {
        userId: "userid",
        selectedDevice: {
          name: "Home",
          dId: "8888",
          templateName: "Power Sensor",
          templateId: "984237562348756ldksjfh",
          saverRule: false
        },
        variableFullName: "Pump",
        variable: "var1",
        variableType: "output",
        icon: "fa-sun",
        column: "col-4",
        widget: "button",
        class: "danger",
        message: "{'fanstatus': 'stop'}"
      },


    };
  },

  mounted() {
    this.getTemplates();
  },

  methods: {
    //Get Templates
    async getTemplates() {
      const axiosHeaders = {
        headers: {
          token: this.$store.state.auth.token
        }
      };

      try {
        const res = await this.$axios.get("/template", axiosHeaders);
        console.log(res.data);

        if (res.data.status == "success") {
          this.templates = res.data.data;
        }
      } catch (error) {
        this.$notify({
          type: "danger",
          icon: "tim-icons icon-alert-circle-exc",
          message: "Error mostrar plantillas..."
        });
        console.log(error);
        return;
      }
    },

    //Save Template
    async saveTemplate() {
      const axiosHeaders = {
        headers: {
          token: this.$store.state.auth.token
        }
      };

      console.log(axiosHeaders);

      const toSend = {
        template: {
          name: this.templateName,
          description: this.templateDescription,
          widgets: this.widgets
        }
      };

      try {
        const res = await this.$axios.post("/template", toSend, axiosHeaders);

        if (res.data.status == "success") {
          this.$notify({
            type: "success",
            icon: "tim-icons icon-alert-circle-exc",
            message: "Plantilla Creada!"
          });
          this.getTemplates();

          this.widgets = [];
        }
      } catch (error) {
        this.$notify({
          type: "danger",
          icon: "tim-icons icon-alert-circle-exc",
          message: "Error creando plantilla..."
        });
        console.log(error);
        return;
      }
    },

    //Delete Template
    async deleteTemplate(template) {

      
      const axiosHeaders = {
        headers: {
          token: this.$store.state.auth.token
        },
        params:{
          templateId:template._id
        }
      };

      console.log(axiosHeaders);

      try {

        const res = await this.$axios.delete("/template", axiosHeaders);

        console.log(res.data)

        if (res.data.status == "fail" && res.data.error == "template in use") {

          this.$notify({
            type: "danger",
            icon: "tim-icons icon-alert-circle-exc",
            message: template.name + " esta en uso. Primero elimina la plantilla relacionada!"
          });
          
          return;
        }

        if (res.data.status == "success") {
          this.$notify({
            type: "success",
            icon: "tim-icons icon-check-2",
            message: template.name + " Eliminada!"
          });
          
          this.getTemplates();
        }
      } catch (error) {
        this.$notify({
          type: "danger",
          icon: "tim-icons icon-alert-circle-exc",
          message: "Error mostrar plantillas..."
        });
        console.log(error);
        return;
      }
    },

    //Add Widget
    addNewWidget() {
      if (this.widgetType == "numberchart") {
        this.ncConfig.variable = this.makeid(10);
        this.widgets.push(JSON.parse(JSON.stringify(this.ncConfig)));
      }

      if (this.widgetType == "switch") {
        this.iotSwitchConfig.variable = this.makeid(10);
        this.widgets.push(JSON.parse(JSON.stringify(this.iotSwitchConfig)));
      }

      if (this.widgetType == "button") {
        this.configButton.variable = this.makeid(10);
        this.widgets.push(JSON.parse(JSON.stringify(this.configButton)));
      }

      if (this.widgetType == "indicator") {
        this.iotIndicatorConfig.variable = this.makeid(10);
        this.widgets.push(JSON.parse(JSON.stringify(this.iotIndicatorConfig)));
      }

    },

    //Delete Widget
    deleteWidget(index) {
      this.widgets.splice(index, 1);
    },

    makeid(length) {
      var result = "";
      var characters =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
      var charactersLength = characters.length;
      for (var i = 0; i < length; i++) {
        result += characters.charAt(
          Math.floor(Math.random() * charactersLength)
        );
      }
      return result;
    }
  }
};
</script>
