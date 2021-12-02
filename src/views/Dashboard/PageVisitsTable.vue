<template>
  <div class="card border-none" style="background: rgb(23, 43, 77)">
    <div
      class="card-header border-none"
      style="background: rgb(23, 43, 77) !important"
    >
      <div class="row align-items-center">
        <div class="col">
          <h3 class="mb-0 text-white">Block Details</h3>
        </div>
        <div class="col text-right">
          <a href="#!" class="btn btn-sm btn-primary">See all</a>
        </div>
      </div>
    </div>

    <div class="table-responsive">
      <base-table
        thead-classes="thead-light"
        :data="tableData"
        style="background: rgb(23, 43, 77) !important"
      >
        <template v-slot:columns style="background: rgb(23, 43, 77)">
          <th>BLock</th>
          <th>Number</th>
          <th></th>
          <th>Bounce rate</th>
          <th>Status</th>
        </template>

        <template v-slot:default="row">
          <th scope="row" class="text-white">
            {{ row.item.page }}
          </th>
          <td class="text-white">
            {{ row.item.visitors }}
          </td>
          <td class="text-white">
            {{ row.item.unique }}
          </td>
          <td class="text-white">
            <i
              class="fas fa-arrow-up text-success mr-3"
              :class="
                row.item.bounceRateDirection === 'up'
                  ? 'text-success'
                  : 'text-danger'
              "
            >
            </i>
            {{ row.item.bounceRate }}
          </td>
          <td>
            <!-- {{ row.item.unique }} -->
            <div class="custom-control custom-switch px-0">
              <label class="switch">
                <input type="checkbox" @click="toggleCheckbox" />
                <div class="slider round"></div>
              </label>
            </div>
          </td>
        </template>
      </base-table>
    </div>
  </div>
</template>
<script>
export default {
  name: "page-visits-table",
  data() {
    return {
      tableData: [
        {
          page: "Block One",
          visitors: "4,569",
          unique: "340",
          bounceRate: "46,53%",
          bounceRateDirection: "up",
        },
        {
          page: "Block Two",
          visitors: "3,985",
          unique: "319",
          bounceRate: "46,53%",
          bounceRateDirection: "down",
        },
        {
          page: "Block Three",
          visitors: "3,513",
          unique: "294",
          bounceRate: "36,49%",
          bounceRateDirection: "down",
        },
        {
          page: "Block Four",
          visitors: "2,050",
          unique: "147",
          bounceRate: "50,87%",
          bounceRateDirection: "up",
        },
        {
          page: "Block Five",
          visitors: "1,795",
          unique: "190",
          bounceRate: "46,53%",
          bounceRateDirection: "down",
        },
      ],
    };
  },
};
</script>
<style scoped>
body {
  text-align: center;
  background: #51c3a0;
  padding: 50px;
}
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.switch input {
  display: none;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #32325d;
}

input:focus + .slider {
  box-shadow: 0 0 1px #32325d;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>
