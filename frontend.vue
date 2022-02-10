<template>
  <div class="font-main text-white bg-blue-verydark">
    <main class="flex flex-col relative min-h-screen mx-auto">
      <section class="px-5">
        <div class="flex flex-col mx-auto w-screen md:max-w-7xl">
          <div class="flex flex-col md:max-w-1000 mx-auto w-full mb-10rem">
            <div>
              <header
                class="flex justify-between items-center md:justify-end space-x-25 py-10 px-10 md:py-15 md:px-0"
              >
                <div
                  class="hidden md:flex justify-center items-center mr-auto cursor-pointer"
                >
                  <img src="../assets/logo.png" class="max-w-24 max-h-24" />
                </div>

                <div
                  v-if="isConnected"
                  class="truncate max-w-170 text-18 text-yellow"
                >
                  {{ account }}
                </div>
                <div
                  @click.prevent="connect"
                  class="flex items-center max-h-35 shadow-sm px-10 py-6 rounded-md space-x-10 cursor-pointer transition duration-300 text-14 md:text-16 text-white"
                  :class="{
                    'bg-green-600 hover:bg-green-400 font-bold': isConnected,
                    'bg-red hover:bg-red-light': !isConnected,
                  }"
                >
                  <svg
                    class="MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-vubbuv w-6 h-6 text-white"
                    focusable="false"
                    viewBox="0 0 24 24"
                    aria-hidden="true"
                    data-testid="AccountBalanceWalletIcon"
                    fill="#e5dede"
                  >
                    <path
                      d="M21 18v1c0 1.1-.9 2-2 2H5c-1.11 0-2-.9-2-2V5c0-1.1.89-2 2-2h14c1.1 0 2 .9 2 2v1h-9c-1.11 0-2 .9-2 2v8c0 1.1.89 2 2 2h9zm-9-2h10V8H12v8zm4-2.5c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5z"
                    ></path></svg
                  ><span>
                    {{ isConnected ? 'Connected' : 'Connect Wallet' }}
                  </span>
                </div>
              </header>
            </div>
            <div
              class="flex md:justify-center items-center space-x-10 bg-blue-light shadow-md rounded-md p-5"
            >
              <svg
                class="MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-vubbuv w-6 h-6"
                focusable="false"
                viewBox="0 0 24 24"
                aria-hidden="true"
                data-testid="InfoIcon"
                fill="#e5dede"
              >
                <path
                  d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"
                ></path></svg
              ><span
                >Ensure you are at
                <a
                  _target="_blank"
                  href="https://zeusnode.finance"
                  class="text-blue-300"
                  >https://zeusnode.finance</a
                ></span
              >
            </div>
            <div class="w-full justify-center items-center pt-3rem">
              <div class="flex flex-col">
                <div class="font-bold text-20 mx-3 md:mx-0">
                  Welcome to Zeus
                </div>
                <div class="text-gray mx-3 md:mx-0">
                  <!-- eslint-disable -->
                  You will see, control, and activate Zeus Nodes from this
                  panel. You will also be able to view the number of rewards
                  that have been awarded and claim them. If desired, you can use
                  them to establish additional Zeus-Nodes, up to a maximum of
                  100 per wallet.
                </div>
                <button @click="buy"
                  class="mx-3 md:mx-0 mt-2 h-8 max-w-40 bg-green-600 w-40 font-semibold hover:bg-green-900 drop-shadow-lg rounded-md text-white text-sm py-1 transition hover:text-white"
                >
                  Buy ZEUS
                </button>
              </div>
            </div>

            <div class="mx-3">
               <div class="flex mt-10">
                 <span class="font-bold mr-3">Join us: </span>
                <a
                  href="https://twitter.com/zeus_node?s=21"
                  target="_blank"
                  class="mr-2"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 48 48"
                    width="30px"
                    height="30px"
                  >
                    <path
                      fill="#03A9F4"
                      d="M42,12.429c-1.323,0.586-2.746,0.977-4.247,1.162c1.526-0.906,2.7-2.351,3.251-4.058c-1.428,0.837-3.01,1.452-4.693,1.776C34.967,9.884,33.05,9,30.926,9c-4.08,0-7.387,3.278-7.387,7.32c0,0.572,0.067,1.129,0.193,1.67c-6.138-0.308-11.582-3.226-15.224-7.654c-0.64,1.082-1,2.349-1,3.686c0,2.541,1.301,4.778,3.285,6.096c-1.211-0.037-2.351-0.374-3.349-0.914c0,0.022,0,0.055,0,0.086c0,3.551,2.547,6.508,5.923,7.181c-0.617,0.169-1.269,0.263-1.941,0.263c-0.477,0-0.942-0.054-1.392-0.135c0.94,2.902,3.667,5.023,6.898,5.086c-2.528,1.96-5.712,3.134-9.174,3.134c-0.598,0-1.183-0.034-1.761-0.104C9.268,36.786,13.152,38,17.321,38c13.585,0,21.017-11.156,21.017-20.834c0-0.317-0.01-0.633-0.025-0.945C39.763,15.197,41.013,13.905,42,12.429"
                    />
                  </svg>
                </a>
                <a
                  href="https://discord.gg/PJeVKvJ8"
                  target="_blank"
                  class="text-white"
                >
                  <svg
                    fill="currentColor"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    width="30px"
                    height="30px"
                  >
                    <path
                      d="M 9.1367188 3.8691406 C 9.1217187 3.8691406 9.1067969 3.8700938 9.0917969 3.8710938 C 8.9647969 3.8810937 5.9534375 4.1403594 4.0234375 5.6933594 C 3.0154375 6.6253594 1 12.073203 1 16.783203 C 1 16.866203 1.0215 16.946531 1.0625 17.019531 C 2.4535 19.462531 6.2473281 20.102859 7.1113281 20.130859 L 7.1269531 20.130859 C 7.2799531 20.130859 7.4236719 20.057594 7.5136719 19.933594 L 8.3886719 18.732422 C 6.0296719 18.122422 4.8248594 17.086391 4.7558594 17.025391 C 4.5578594 16.850391 4.5378906 16.549563 4.7128906 16.351562 C 4.8068906 16.244563 4.9383125 16.189453 5.0703125 16.189453 C 5.1823125 16.189453 5.2957188 16.228594 5.3867188 16.308594 C 5.4157187 16.334594 7.6340469 18.216797 11.998047 18.216797 C 16.370047 18.216797 18.589328 16.325641 18.611328 16.306641 C 18.702328 16.227641 18.815734 16.189453 18.927734 16.189453 C 19.059734 16.189453 19.190156 16.243562 19.285156 16.351562 C 19.459156 16.549563 19.441141 16.851391 19.244141 17.025391 C 19.174141 17.087391 17.968375 18.120469 15.609375 18.730469 L 16.484375 19.933594 C 16.574375 20.057594 16.718094 20.130859 16.871094 20.130859 L 16.886719 20.130859 C 17.751719 20.103859 21.5465 19.463531 22.9375 17.019531 C 22.9785 16.947531 23 16.866203 23 16.783203 C 23 12.073203 20.984172 6.624875 19.951172 5.671875 C 18.047172 4.140875 15.036203 3.8820937 14.908203 3.8710938 C 14.895203 3.8700938 14.880188 3.8691406 14.867188 3.8691406 C 14.681188 3.8691406 14.510594 3.9793906 14.433594 4.1503906 C 14.427594 4.1623906 14.362062 4.3138281 14.289062 4.5488281 C 15.548063 4.7608281 17.094141 5.1895937 18.494141 6.0585938 C 18.718141 6.1975938 18.787437 6.4917969 18.648438 6.7167969 C 18.558438 6.8627969 18.402188 6.9433594 18.242188 6.9433594 C 18.156188 6.9433594 18.069234 6.9200937 17.990234 6.8710938 C 15.584234 5.3800938 12.578 5.3046875 12 5.3046875 C 11.422 5.3046875 8.4157187 5.3810469 6.0117188 6.8730469 C 5.9327188 6.9210469 5.8457656 6.9433594 5.7597656 6.9433594 C 5.5997656 6.9433594 5.4425625 6.86475 5.3515625 6.71875 C 5.2115625 6.49375 5.2818594 6.1985938 5.5058594 6.0585938 C 6.9058594 5.1905937 8.4528906 4.7627812 9.7128906 4.5507812 C 9.6388906 4.3147813 9.5714062 4.1643437 9.5664062 4.1523438 C 9.4894063 3.9813438 9.3217188 3.8691406 9.1367188 3.8691406 z M 12 7.3046875 C 12.296 7.3046875 14.950594 7.3403125 16.933594 8.5703125 C 17.326594 8.8143125 17.777234 8.9453125 18.240234 8.9453125 C 18.633234 8.9453125 19.010656 8.8555 19.347656 8.6875 C 19.964656 10.2405 20.690828 12.686219 20.923828 15.199219 C 20.883828 15.143219 20.840922 15.089109 20.794922 15.037109 C 20.324922 14.498109 19.644687 14.191406 18.929688 14.191406 C 18.332687 14.191406 17.754078 14.405437 17.330078 14.773438 C 17.257078 14.832437 15.505 16.21875 12 16.21875 C 8.496 16.21875 6.7450313 14.834687 6.7070312 14.804688 C 6.2540312 14.407687 5.6742656 14.189453 5.0722656 14.189453 C 4.3612656 14.189453 3.6838438 14.494391 3.2148438 15.025391 C 3.1658438 15.080391 3.1201719 15.138266 3.0761719 15.197266 C 3.3091719 12.686266 4.0344375 10.235594 4.6484375 8.6835938 C 4.9864375 8.8525938 5.3657656 8.9433594 5.7597656 8.9433594 C 6.2217656 8.9433594 6.6724531 8.8143125 7.0644531 8.5703125 C 9.0494531 7.3393125 11.704 7.3046875 12 7.3046875 z M 8.890625 10.044922 C 7.966625 10.044922 7.2167969 10.901031 7.2167969 11.957031 C 7.2167969 13.013031 7.965625 13.869141 8.890625 13.869141 C 9.815625 13.869141 10.564453 13.013031 10.564453 11.957031 C 10.564453 10.900031 9.815625 10.044922 8.890625 10.044922 z M 15.109375 10.044922 C 14.185375 10.044922 13.435547 10.901031 13.435547 11.957031 C 13.435547 13.013031 14.184375 13.869141 15.109375 13.869141 C 16.034375 13.869141 16.783203 13.013031 16.783203 11.957031 C 16.783203 10.900031 16.033375 10.044922 15.109375 10.044922 z"
                    />
                  </svg>
                </a>
                <a class="ml-2 text-white" href="https://medium.com/@ZeusNode">
                  <svg
                    fill="currentColor"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 50 50"
                    width="28px"
                    height="28px"
                  >
                    <path
                      d="M 5 4 A 1.0001 1.0001 0 0 0 4 5 L 4 45 A 1.0001 1.0001 0 0 0 5 46 L 45 46 A 1.0001 1.0001 0 0 0 46 45 L 46 5 A 1.0001 1.0001 0 0 0 45 4 L 5 4 z M 6 6 L 44 6 L 44 44 L 6 44 L 6 6 z M 11 13 L 11 13.5 L 12.857422 16 C 12.949422 16.109 13 16.246672 13 16.388672 L 13 31.5 C 13 31.721 12.923203 31.935422 12.783203 32.107422 L 10 35.546875 L 10 36 L 18 36 L 18 35.546875 L 15.214844 32.087891 C 15.075844 31.916891 15 31.701422 15 31.482422 L 15 18.375 L 23.304688 36 L 24.847656 36 L 24.853516 35.980469 L 32 17.878906 L 32 32.75 C 32 32.91 31.935312 33.063734 31.820312 33.177734 L 29 35.546875 L 29 36 L 40 36 L 40 35.546875 L 38.179688 33.177734 C 38.064687 33.063734 38 32.91 38 32.75 L 38 16.125 C 38 15.965 38.064687 15.811266 38.179688 15.697266 L 40 13.5 L 40 13 L 31.775391 13 L 25.996094 27.642578 L 19.097656 13 L 11 13 z M 15.621094 15 L 17.828125 15 L 24.988281 30.195312 L 23.982422 32.744141 L 23.980469 32.744141 L 15.621094 15 z M 34 15 L 36.257812 15 C 36.090813 15.348 36 15.735 36 16.125 L 36 32.75 C 36 33.188 36.113266 33.619 36.322266 34 L 33.677734 34 C 33.886734 33.619 34 33.188 34 32.75 L 34 17.878906 L 34 15 z"
                    />
                  </svg>
                </a>
              </div>
            </div>

            <div
              class="grid grid-cols-1 gap-2 md:grid-none md:flex justify-center items-center md:space-x-1rem pt-3rem"
            >
              <div
                class="flex justify-between items-center border border-gray-400 p-10 shadow-md rounded-md space-x-2rem w-full"
              >
                <div class="flex items-center space-x-20">
                  <div class="pl-10 text-blue-300">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="24"
                      height="24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      class="feather feather-hexagon"
                    >
                      <path
                        d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"
                      ></path>
                    </svg>
                  </div>
                  <div class="flex flex-col">
                    <div class="text-base font-bold">
                      <span>{{ userTotalNodes }}/100</span>
                    </div>
                    <div class="text-14 text-blue-300">Owned Nodes</div>
                  </div>
                </div>
              </div>
              <div
                class="flex justify-between items-center border border-gray-400 p-10 shadow-md rounded-md space-x-2rem w-full"
              >
                <div class="flex items-center space-x-20">
                  <div class="pl-10 text-red-400">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="24"
                      height="24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      class="feather feather-git-merge"
                    >
                      <circle cx="18" cy="18" r="3"></circle>
                      <circle cx="6" cy="6" r="3"></circle>
                      <path d="M6 21V9a9 9 0 0 0 9 9"></path>
                    </svg>
                  </div>
                  <div class="flex flex-col">
                    <div class="text-base font-bold">
                      <span> {{ totalCreatedNodes }} </span>
                    </div>
                    <div class="text-14 text-red-400">Total Nodes</div>
                  </div>
                </div>
              </div>
              <div
                class="border border-gray-400 items-center p-10 shadow-md rounded-md space-x-2rem w-full"
              >
                <div class="flex justify-between">
                  <div class="flex items-center space-x-20">
                    <div class="pl-10 text-teal">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        class="h-6 w-6"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke="currentColor"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          stroke-width="2"
                          d="M13 10V3L4 14h7v7l9-11h-7z"
                        />
                      </svg>
                    </div>
                    <div class="flex flex-col">
                      <div class="text-base flex">
                        <span class="mr-3 font-bold">
                          {{ parseFloat(totalRewards).toFixed(2) }}
                          <span class="text-white">ZEUS</span></span
                        >
                      </div>
                      <div class="flex justify-between">
                        <div class="text-14 text-teal mr-5">Total Rewards</div>
                      </div>
                    </div>
                  </div>
                  <div v-if="totalRewards > 0">
                    <button
                      :disabled="claiming"
                      @click.prevent="claimAllReward"
                      class="bg-green-700 mt-2 px-2 py-1 hover:bg-green-800 rounded"
                    >
                      Claim all
                    </button>
                  </div>
                </div>
              </div>
            </div>

            <div
              class="flex flex-col justify-center items-center w-full p-30 pt-4rem shadow-md rounded-md mt-3rem"
            >
              <div class="text-blue-200">Create a node</div>
              <!-- <div>
                Select one of the 3 available
                <span class="font-bold">Node Tiers</span> to get started
              </div> -->
              <div class="mx-auto my-5 border border-teal rounded-lg">
                <div
                  class="border-double relative border-teal bg-black rounded-full w-52 h-52"
                >
                  <div class="bg">
                    <img
                      src="../assets/hand.png"
                      class="m-auto max-w-52 max-h-52"
                    />
                  </div>
                  <div class="lightning absolute top-0 right-14">
                    <img
                      src="../assets/hand.png"
                      class="flashit m-auto max-w-52 max-h-52"
                    />
                  </div>
                </div>
                <span class="text-white font-bold flex justify-center"
                  >ZEUS</span
                >

                <div class="text-blue-200 text-sm flex justify-center">
                  {{ pricePerNode }} ZEUS per node
                </div>
                <div class="mb-3 text-sm text-blue-200 flex justify-center">
                  Earn {{ rewardPerNode }}
                  <span class="font-semibold text-white mx-1">ZEUS</span> per
                  day
                </div>
              </div>
              <div
                class="md:flex items-center justify-center md:space-x-2rem pt-2rem"
              >
                <div
                  class="flex flex-col justify-center items-center p-15 rounded-md max-w-200"
                >
                  <div class="text-base text-white-400">
                    {{ parseFloat(balanceOf).toFixed(2) }} ZEUS
                  </div>
                </div>

                <div
                  class="flex flex-col justify-center items-center p-15 rounded-md max-w-200"
                >
                  <button
                    :disabled="approving"
                    @click.prevent="approve"
                    class="px-2rem h-8 font-semibold hover:bg-gray-900 drop-shadow-lg rounded-md border border-teal text-white text-16 py-1 transition hover:text-white"
                  >
                    {{ approving ? 'Approving...' : 'Approve' }}
                  </button>
                </div>
              </div>
              <div class="text-14 w-80 text-white">
                Please approve the contract before creating a node if this is
                your first interaction with ZEUS.
              </div>
              <div class="flex my-3rem space-x-1rem">
                <input
                  v-model="name"
                  class="bg-blue-verydark h-10 border border-gray-200 rounded-lg text-center"
                  placeholder="Node Name"
                /><button
                  @click.prevent="createNode"
                  :disabled="disabled"
                  class="h-11 flex items-center justify-center py-6 px-20 bg-gray-light rounded-md transition duration-300 hover:bg-green-700"
                >
                  <svg
                    class="MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-vubbuv w-6 h-6"
                    focusable="false"
                    viewBox="0 0 24 24"
                    aria-hidden="true"
                    data-testid="AirIcon"
                    fill="#e5dede"
                  >
                    <path
                      d="M14.5 17c0 1.65-1.35 3-3 3s-3-1.35-3-3h2c0 .55.45 1 1 1s1-.45 1-1-.45-1-1-1H2v-2h9.5c1.65 0 3 1.35 3 3zM19 6.5C19 4.57 17.43 3 15.5 3S12 4.57 12 6.5h2c0-.83.67-1.5 1.5-1.5s1.5.67 1.5 1.5S16.33 8 15.5 8H2v2h13.5c1.93 0 3.5-1.57 3.5-3.5zm-.5 4.5H2v2h16.5c.83 0 1.5.67 1.5 1.5s-.67 1.5-1.5 1.5v2c1.93 0 3.5-1.57 3.5-3.5S20.43 11 18.5 11z"
                    ></path></svg
                  ><span class="ml-1">
                    {{ disabled ? 'Creating Node' : 'Create Node' }}
                  </span>
                </button>
              </div>

              <div class="w-96 md:w-auto" v-if="nodes.length > 0">
                <div class="mb-4 text-xl text-center text-white font-bold">
                  Node History
                </div>

                <div class="flex flex-col text-white">
                  <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
                    <div class="py-2 inline-block min-w-full sm:px-6 lg:px-8">
                      <div class="overflow-hidden">
                        <table class="min-w-full">
                          <thead class="border-b">
                            <tr>
                              <th
                                scope="col"
                                class="text-sm font-medium px-6 py-4 text-left"
                              >
                                #
                              </th>
                              <th
                                scope="col"
                                class="text-sm font-medium px-6 py-4 text-left"
                              >
                                Name
                              </th>
                              <th
                                scope="col"
                                class="text-sm font-medium px-6 py-4 text-left"
                              >
                                Created at
                              </th>
                              <th
                                scope="col"
                                class="text-sm font-medium px-6 py-4 text-left"
                              >
                                Rewards
                              </th>
                              <th
                                scope="col"
                                class="text-sm font-medium px-6 py-4 text-left"
                              >
                                Status
                              </th>
                              <th
                                scope="col"
                                class="text-sm font-medium px-6 py-4 text-left"
                              >
                                Next reward at
                              </th>
                            </tr>
                          </thead>
                          <tbody>
                            <tr
                              class="border-b"
                              v-for="(node, index) in nodes"
                              :key="index"
                            >
                              <td
                                class="px-6 py-4 whitespace-nowrap text-sm font-medium"
                              >
                                {{ index + 1 }}
                              </td>
                              <td
                                class="text-sm font-light px-6 py-4 whitespace-nowrap"
                              >
                                {{ node.name }}
                              </td>
                              <td
                                class="text-sm font-light px-6 py-4 whitespace-nowrap"
                              >
                                {{ node.time }}
                              </td>
                              <td
                                class="text-sm font-light px-6 py-4 whitespace-nowrap"
                              >
                                {{ parseFloat(node.amount).toFixed(2) }}
                                ZEUS
                              </td>
                              <td
                                :class="{
                                  'text-green-400': node.status === 1,
                                  'text-yellow-400': node.status === 0,
                                }"
                                class="text-sm font-light px-6 py-4 whitespace-nowrap"
                              >
                                {{ node.status === 1 ? 'Running' : 'Expired' }}
                              </td>
                              <td
                                :id="`nextRewardTime${index}`"
                                class="text-sm font-light px-6 pt-4 whitespace-nowrap"
                              >
                                <vue3-flip-countdown
                                  countdownSize="0.9rem"
                                  labelSize=".5rem"
                                  :showDays="false"
                                  :deadlineDate="node.lastClaimTime
                                  "
                                  labelColor="white"
                                  mainColor="#42baed"
                                  secondFlipColor="#42baed"
                                  @timeElapsed="reloadTime"
                                />
                              </td>
                              <td
                                class="text-sm font-light py-4 whitespace-nowrap"
                              >
                                <button
                                  :disabled="claiming"
                                  @click.prevent="claimReward(node.blocktime)"
                                  class="bg-green-700 px-2 py-1 hover:bg-green-800 rounded"
                                >
                                  Claim
                                </button>
                              </td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <hr>
              <div class="flex text-center md:max-w-3xl mt-20">
                <div>
                  <h4 class="font-bold">Join Our Community</h4>
                  <p>
                    <span class="font-semibold">Have questions or want to get a feel of the community before
                    diving in?</span> ‍ <p>Then join other Olympians on Twitter or Discord
                    to learn more about Zeus Nodes, the future of DeFi</p>
                  </p>
                </div>
              </div>
              <div class="flex justify-center mt-5">
                <a
                  href="https://twitter.com/zeus_node?s=21"
                  target="_blank"
                  class="mr-2"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 48 48"
                    width="30px"
                    height="30px"
                  >
                    <path
                      fill="#03A9F4"
                      d="M42,12.429c-1.323,0.586-2.746,0.977-4.247,1.162c1.526-0.906,2.7-2.351,3.251-4.058c-1.428,0.837-3.01,1.452-4.693,1.776C34.967,9.884,33.05,9,30.926,9c-4.08,0-7.387,3.278-7.387,7.32c0,0.572,0.067,1.129,0.193,1.67c-6.138-0.308-11.582-3.226-15.224-7.654c-0.64,1.082-1,2.349-1,3.686c0,2.541,1.301,4.778,3.285,6.096c-1.211-0.037-2.351-0.374-3.349-0.914c0,0.022,0,0.055,0,0.086c0,3.551,2.547,6.508,5.923,7.181c-0.617,0.169-1.269,0.263-1.941,0.263c-0.477,0-0.942-0.054-1.392-0.135c0.94,2.902,3.667,5.023,6.898,5.086c-2.528,1.96-5.712,3.134-9.174,3.134c-0.598,0-1.183-0.034-1.761-0.104C9.268,36.786,13.152,38,17.321,38c13.585,0,21.017-11.156,21.017-20.834c0-0.317-0.01-0.633-0.025-0.945C39.763,15.197,41.013,13.905,42,12.429"
                    />
                  </svg>
                </a>
                <a
                  href="https://discord.gg/PJeVKvJ8"
                  target="_blank"
                  class="text-white"
                >
                  <svg
                    fill="currentColor"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    width="30px"
                    height="30px"
                  >
                    <path
                      d="M 9.1367188 3.8691406 C 9.1217187 3.8691406 9.1067969 3.8700938 9.0917969 3.8710938 C 8.9647969 3.8810937 5.9534375 4.1403594 4.0234375 5.6933594 C 3.0154375 6.6253594 1 12.073203 1 16.783203 C 1 16.866203 1.0215 16.946531 1.0625 17.019531 C 2.4535 19.462531 6.2473281 20.102859 7.1113281 20.130859 L 7.1269531 20.130859 C 7.2799531 20.130859 7.4236719 20.057594 7.5136719 19.933594 L 8.3886719 18.732422 C 6.0296719 18.122422 4.8248594 17.086391 4.7558594 17.025391 C 4.5578594 16.850391 4.5378906 16.549563 4.7128906 16.351562 C 4.8068906 16.244563 4.9383125 16.189453 5.0703125 16.189453 C 5.1823125 16.189453 5.2957188 16.228594 5.3867188 16.308594 C 5.4157187 16.334594 7.6340469 18.216797 11.998047 18.216797 C 16.370047 18.216797 18.589328 16.325641 18.611328 16.306641 C 18.702328 16.227641 18.815734 16.189453 18.927734 16.189453 C 19.059734 16.189453 19.190156 16.243562 19.285156 16.351562 C 19.459156 16.549563 19.441141 16.851391 19.244141 17.025391 C 19.174141 17.087391 17.968375 18.120469 15.609375 18.730469 L 16.484375 19.933594 C 16.574375 20.057594 16.718094 20.130859 16.871094 20.130859 L 16.886719 20.130859 C 17.751719 20.103859 21.5465 19.463531 22.9375 17.019531 C 22.9785 16.947531 23 16.866203 23 16.783203 C 23 12.073203 20.984172 6.624875 19.951172 5.671875 C 18.047172 4.140875 15.036203 3.8820937 14.908203 3.8710938 C 14.895203 3.8700938 14.880188 3.8691406 14.867188 3.8691406 C 14.681188 3.8691406 14.510594 3.9793906 14.433594 4.1503906 C 14.427594 4.1623906 14.362062 4.3138281 14.289062 4.5488281 C 15.548063 4.7608281 17.094141 5.1895937 18.494141 6.0585938 C 18.718141 6.1975938 18.787437 6.4917969 18.648438 6.7167969 C 18.558438 6.8627969 18.402188 6.9433594 18.242188 6.9433594 C 18.156188 6.9433594 18.069234 6.9200937 17.990234 6.8710938 C 15.584234 5.3800938 12.578 5.3046875 12 5.3046875 C 11.422 5.3046875 8.4157187 5.3810469 6.0117188 6.8730469 C 5.9327188 6.9210469 5.8457656 6.9433594 5.7597656 6.9433594 C 5.5997656 6.9433594 5.4425625 6.86475 5.3515625 6.71875 C 5.2115625 6.49375 5.2818594 6.1985938 5.5058594 6.0585938 C 6.9058594 5.1905937 8.4528906 4.7627812 9.7128906 4.5507812 C 9.6388906 4.3147813 9.5714062 4.1643437 9.5664062 4.1523438 C 9.4894063 3.9813438 9.3217188 3.8691406 9.1367188 3.8691406 z M 12 7.3046875 C 12.296 7.3046875 14.950594 7.3403125 16.933594 8.5703125 C 17.326594 8.8143125 17.777234 8.9453125 18.240234 8.9453125 C 18.633234 8.9453125 19.010656 8.8555 19.347656 8.6875 C 19.964656 10.2405 20.690828 12.686219 20.923828 15.199219 C 20.883828 15.143219 20.840922 15.089109 20.794922 15.037109 C 20.324922 14.498109 19.644687 14.191406 18.929688 14.191406 C 18.332687 14.191406 17.754078 14.405437 17.330078 14.773438 C 17.257078 14.832437 15.505 16.21875 12 16.21875 C 8.496 16.21875 6.7450313 14.834687 6.7070312 14.804688 C 6.2540312 14.407687 5.6742656 14.189453 5.0722656 14.189453 C 4.3612656 14.189453 3.6838438 14.494391 3.2148438 15.025391 C 3.1658438 15.080391 3.1201719 15.138266 3.0761719 15.197266 C 3.3091719 12.686266 4.0344375 10.235594 4.6484375 8.6835938 C 4.9864375 8.8525938 5.3657656 8.9433594 5.7597656 8.9433594 C 6.2217656 8.9433594 6.6724531 8.8143125 7.0644531 8.5703125 C 9.0494531 7.3393125 11.704 7.3046875 12 7.3046875 z M 8.890625 10.044922 C 7.966625 10.044922 7.2167969 10.901031 7.2167969 11.957031 C 7.2167969 13.013031 7.965625 13.869141 8.890625 13.869141 C 9.815625 13.869141 10.564453 13.013031 10.564453 11.957031 C 10.564453 10.900031 9.815625 10.044922 8.890625 10.044922 z M 15.109375 10.044922 C 14.185375 10.044922 13.435547 10.901031 13.435547 11.957031 C 13.435547 13.013031 14.184375 13.869141 15.109375 13.869141 C 16.034375 13.869141 16.783203 13.013031 16.783203 11.957031 C 16.783203 10.900031 16.033375 10.044922 15.109375 10.044922 z"
                    />
                  </svg>
                </a>
                <a class="ml-2 text-white" href="https://medium.com/@ZeusNode">
                  <svg
                    fill="currentColor"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 50 50"
                    width="28px"
                    height="28px"
                  >
                    <path
                      d="M 5 4 A 1.0001 1.0001 0 0 0 4 5 L 4 45 A 1.0001 1.0001 0 0 0 5 46 L 45 46 A 1.0001 1.0001 0 0 0 46 45 L 46 5 A 1.0001 1.0001 0 0 0 45 4 L 5 4 z M 6 6 L 44 6 L 44 44 L 6 44 L 6 6 z M 11 13 L 11 13.5 L 12.857422 16 C 12.949422 16.109 13 16.246672 13 16.388672 L 13 31.5 C 13 31.721 12.923203 31.935422 12.783203 32.107422 L 10 35.546875 L 10 36 L 18 36 L 18 35.546875 L 15.214844 32.087891 C 15.075844 31.916891 15 31.701422 15 31.482422 L 15 18.375 L 23.304688 36 L 24.847656 36 L 24.853516 35.980469 L 32 17.878906 L 32 32.75 C 32 32.91 31.935312 33.063734 31.820312 33.177734 L 29 35.546875 L 29 36 L 40 36 L 40 35.546875 L 38.179688 33.177734 C 38.064687 33.063734 38 32.91 38 32.75 L 38 16.125 C 38 15.965 38.064687 15.811266 38.179688 15.697266 L 40 13.5 L 40 13 L 31.775391 13 L 25.996094 27.642578 L 19.097656 13 L 11 13 z M 15.621094 15 L 17.828125 15 L 24.988281 30.195312 L 23.982422 32.744141 L 23.980469 32.744141 L 15.621094 15 z M 34 15 L 36.257812 15 C 36.090813 15.348 36 15.735 36 16.125 L 36 32.75 C 36 33.188 36.113266 33.619 36.322266 34 L 33.677734 34 C 33.886734 33.619 34 33.188 34 32.75 L 34 17.878906 L 34 15 z"
                    />
                  </svg>
                </a>
              </div>
              <hr>
              <div class="flex space-x-3rem mt-32">
                <div><a target="_blank" href="https://zeusnode.finance/disclaimer.html" class="text-sm text-gray">Disclaimer</a></div>
                <div><small class="text-gray">copyright ©Zeus Finance 2022</small></div>
                </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>
<script>
import { getWeb3, getContracts, selectedAccount } from '../utils/getWeb3.js';
import { useToast } from 'vue-toastification';
import moment from 'moment';

export default {
  setup() {
    const toast = useToast();
    return { toast };
  },

  data() {
    return {
      isConnected: false,
      contract: null,
      totalCreatedNodes: 0,
      userTotalNodes: 0,
      name: '',
      disabled: false,
      account: '',
      nodes: [],
      balanceOf: 0,
      approving: false,
      rewardPerNode: 0.0,
      pricePerNode: 0.0,
      totalRewards: 0.0,
      web3: null,
      timer: null,
      enableClaimall: false,
      fakeTotal: 0,
      times: new Set(),
      moment,
      claimTime: null,
      claiming: false,
    };
  },
  methods: {
    buy(){
      const url = "https://traderjoexyz.com/trade?outputCurrency=0x3b8581fc8714e876deb82e77eea88cc8afbcd8ff#/";
      window.open(url, '_blank').focus();
    },
    reloadTime() {
      // const nodes = this.nodes.map((node) => {
      //   const now = new Date();
      //   let expires = moment.unix(node.blocktime).add(20, 'day');
      //   if (this.claimTime < 10000) {
      //     expires = moment.unix(node.blocktime).add(5, 'minute');
      //   }
      //   const nextTime = moment.unix(node.lastClaimTime);
      //   if (now >= nextTime && now < expires) {
      //     node.lastClaimTime = Date.now() / 1000 + 86400;
      //   }
      //   return node;
      // });
      // this.nodes = nodes;
    },
    async connect() {
      try {
        const web3 = await getWeb3();
        this.web3 = web3;
        const { smartContract } = await getContracts(web3);
        let contract = smartContract;
        this.account = selectedAccount;
        this.contract = contract;
        this.isConnected = true;
        let wallet = localStorage.getItem('wallet');
        if (!wallet) {
          this.toast.success('Wallet connected successfully');
        }
        localStorage.setItem('wallet', selectedAccount);
        this.totalCreatedNodes = await contract.methods
          .getTotalCreatedNodes()
          .call();
        this.userTotalNodes = await contract.methods
          .getNodeNumberOf(selectedAccount)
          .call();

        const rewardPerNode = await contract.methods.getRewardPerNode().call();
        const pricePerNode = await contract.methods.getNodePrice().call();

        this.rewardPerNode = parseFloat(rewardPerNode / 10e17).toFixed(2);
        this.pricePerNode = parseFloat(pricePerNode / 10e17).toFixed(2);

        await this.fetchData();
      } catch (error) {
        this.toast.error(error.message);
        this.isConnected = false;
      }
    },
    async fetchData() {
      try {
        if (this.userTotalNodes > 0) {
          const response = await this.contract.methods
            .getNodesNames()
            .call({ from: selectedAccount });
          const nodesCreatime = await this.contract.methods
            .getNodesCreatime()
            .call({ from: selectedAccount });
          const rewardAmounts = await this.contract.methods
            .getNodesRewards()
            .call({ from: selectedAccount });

            const distribute = await this.contract.methods
            .publiDistriRewards()
            .call();
            console.log('calling')
            console.log('dd: ',distribute)

const claimTime = await this.contract.methods.getClaimTime().call();
          const nodesLastClaims = await this.contract.methods
            .getNodesLastClaims()
            .call({ from: selectedAccount });

          // const extraTime = 180;

          const times = nodesCreatime.split('#');
          const amounts = rewardAmounts.split('#');
          const lastClaims = nodesLastClaims.split('#');

          const nodes = response.split('#');
          // const date = new Date();
          for (let i = 0; i < nodes.length; i++) {
            this.nodes = [
              ...this.nodes,
              {
                name: nodes[i],
                time: moment.unix(times[i]).fromNow(),
                blocktime: times[i],
                amount: amounts[i] / 10e17,
                lastClaimTime: new Date(moment.unix(lastClaims[i]).add(claimTime, 'seconds')),
                status: 1,
              },
            ];
          }
          const totalRewards = await this.contract.methods
            .getRewardAmount()
            .call({ from: selectedAccount });
          this.totalRewards = parseFloat(totalRewards / 10e17).toFixed(2);
          
      
        }

        const balanceOf = await this.contract.methods
          .balanceOf(selectedAccount)
          .call();

        this.balanceOf = parseFloat(balanceOf) / 10e17;
      } catch (error) {
        console.log(error)
      }
    },
    async claimReward(blocktime) {
      try {
        this.claiming = true;

        await this.contract.methods
          .cashoutReward(blocktime)
          .send({ from: selectedAccount });
        this.toast.success('successfulÏ');
        window.location.reload();
        this.claiming = false;
      } catch (error) {
        this.claiming = false;
        let e = error?.message.split('.')[1];
        let x = JSON.parse(e);
        this.toast.error(x.message);
      }
    },
    async claimAllReward() {
      // if (this.enableClaimall) {
      //   return this.toast.error('You still have active nodes');
      // }
      try {
         this.claiming = true;
        await this.contract.methods
          .cashoutAll()
          .send({ from: selectedAccount });
        this.toast.success('successful');
         this.claiming = false;
        window.location.reload();
      } catch (error) {
         this.claiming = true;
        let e = error?.message.split('.')[1];
        let x = JSON.parse(e);
        this.toast.error(x.message);
      }
    },
    async approve() {
      try {
        this.approving = true;
        await this.contract.methods
          .approve(selectedAccount, '100000000000000000000000000000')
          .send({ from: selectedAccount });
        this.approving = false;
        this.toast.success('Success');
      } catch (error) {
        this.approving = false;
        this.toast.error(error.message);
      }
    },

    async createNode() {
      try {
        if (this.name == '') {
          return this.toast.error('node name is required');
        }
        if (this.name.trim().length < 4) {
          return this.toast.error('Node name must be a minimus of 4');
        }
        this.disabled = true;
        let res = await this.contract.methods
          .createNodeWithTokens(this.name)
          .send({ from: selectedAccount });
        if (res.status) {
          this.toast.success('Node created successfully');
        }
        this.disabled = false;
        this.name = '';
        window.location.reload();
      } catch (error) {
        this.disabled = false;
        this.toast.error('Failed to create node');
      }
    },
    async loadAccount() {
      let wallet = localStorage.getItem('wallet');
      if (wallet && wallet !== undefined) {
        this.connect();
      } else {
        localStorage.removeItem('wallet');
      }
    },
  },
  created() {
    this.loadAccount();
  },
};
</script>
<style scoped>
.bg {
  width: 100%;
  height: 100%;
  background-position: center center;
  z-index: -2;
}

/* Now the same background, but with brightness filters*/
.lightning {
  background-position: center center;
  -webkit-filter: brightness(3);
  filter: brightness(3);
  -o-filter: brightness(3);
  -moz-filter: brightness(3);
  z-index: 1000;
}

/*Now just a opacity animation*/
.flashit {
  -webkit-animation: flash ease-out 5s infinite;
  -moz-animation: flash ease-out 5s infinite;
  animation: flash ease-out 5s infinite;
  animation-delay: 3s;
}

@-webkit-keyframes flash {
  from {
    opacity: 0;
  }
  92% {
    opacity: 0;
  }
  93% {
    opacity: 0.6;
  }
  94% {
    opacity: 0.2;
  }
  96% {
    opacity: 0.9;
  }
  to {
    opacity: 0;
  }
}

@keyframes flash {
  from {
    opacity: 0;
  }
  92% {
    opacity: 0;
  }
  93% {
    opacity: 0.6;
  }
  94% {
    opacity: 0.2;
  }
  96% {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
</style>
