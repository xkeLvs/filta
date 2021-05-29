<template>
  <div>
    <header class="masthead">
      <div class="container h-100">
        <div class="row h-100 align-items-center">
          <div class="col-12 text-center">
            <h1>Hello Developer!</h1>
            <h1>
              Lorem ipsum dolor sit amet consectetur, adipisicing elit. Neque
              voluptatem magni esse, quo, repellat dignissimos impedit
              cupiditate corrupti aliquid laboriosam omnis exercitationem natus
              eligendi quis consequatur tempore sed fugit possimus!
            </h1>
          </div>
        </div>
      </div>
    </header>
    <div class="container mt-3">
      <div class="row">
        <div class="card p-4 col-md-3 col-sm-12 mt-3 mx-auto">
          <img
            class="card-img-top"
            src="http://via.placeholder.com/400x300"
            alt="Card image"
            style="width: 100%"
          />
          <div class="card-body">
            <p class="card-text">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit
              architecto, perspiciatis aperiam recusandae, voluptatibus saepe
              atque perferendis tempore quam vitae eum magni autem harum
              suscipit et, aliquid est. Veritatis, nostrum.
            </p>
            <a href="#" class="btn border border-dark rounded">READ MORE</a>
          </div>
        </div>
        <div class="card p-4 col-md-3 col-sm-12 mt-3 mx-auto">
          <img
            class="card-img-top"
            src="http://via.placeholder.com/400x300"
            alt="Card image"
            style="width: 100%"
          />
          <div class="card-body">
            <p class="card-text">
              Lorem, ipsum dolor sit amet consectetur adipisicing elit.
              Laudantium possimus, asperiores incidunt pariatur quasi reiciendis
              minima doloribus officia reprehenderit placeat id mollitia, quia,
              voluptatum animi. Pariatur aliquid temporibus quae deserunt?
            </p>
            <a href="#" class="btn border border-dark rounded">READ MORE</a>
          </div>
        </div>

        <div class="card p-4 col-md-3 col-sm-12 mt-3 mx-auto">
          <img
            class="card-img-top"
            src="http://via.placeholder.com/400x300"
            alt="Card image"
            style="width: 100%"
          />
          <div class="card-body">
            <p class="card-text">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit.
              Eligendi, a velit vero tenetur odio cumque voluptas molestiae
              perferendis rerum? Sapiente neque dicta nisi, ullam exercitationem
              vero repellendus dolore dolorum dolores!
            </p>
            <a href="#" class="btn border border-dark rounded">READ MORE</a>
          </div>
        </div>
      </div>
      <div class="mt-3">
        <ul class="nav nav-tabs" id="tabs" role="tablist">
          <li
            class="nav-item"
            role="presentation"
            v-for="(data, index) in dataLists"
            :key="index"
          >
            <button
              class="nav-link"
              :id="'home-tab' + index"
              data-bs-toggle="tab"
              type="button"
              role="tab"
              aria-selected="true"
              v-on:click="getContent(index)"
              :class="currentIndex == index ? 'active' : ''"
            >
              {{ data.title }}
            </button>
          </li>
        </ul>

        <div class="tab-content" id="tabsContent">
          <p v-html="currentContent"></p>
        </div>

        <div class="accordion" id="accordionData">
          <div
            class="accordion-item"
            v-for="(data, index) in dataLists"
            :key="index"
          >
            <h2 class="accordion-header" :id="'data' + index">
              <button
                class="accordion-button collapsed"
                type="button"
                data-bs-toggle="collapse"
                :data-bs-target="'#collapseTarget' + index"
                aria-expanded="false"
                :aria-controls="'collapseTarget' + index"
              >
                {{ data.title }}
              </button>
            </h2>
            <div
              :id="'collapseTarget' + index"
              class="accordion-collapse collapse"
              :aria-labelledby="'data' + index"
              data-bs-parent="#accordionData"
            >
              <div class="accordion-body">
                <p v-html="data.content"></p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Filta",
  data() {
    return {
      dataLists: [
        {
          title: "Section 1",
          content:
            "<p>Maecenas nec semper ante, pellentesque posuere lorem. Nullam ipsum massa, consequat eget urna ut, pulvinar dignissim lorem. Nulla facilisi. Nam mattis eleifend metus. Fusce at commodo lorem. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Phasellus pellentesque elit sem, vel blandit posuere.</p>",
        },
        {
          title: "Section 2",
          content:
            "<p>Mauris a orci sodales, scelerisque velit vitae, gravida nisl. Ut non laoreet eros, vel laoreet nisi. Praesent sed dolor dui. Proin non fringilla quam. Aliquam erat volutpat. Vestibulum vel arcu semper, lobortis turpis ac, ultricies nisi. Praesent id.</p>",
        },
        {
          title: "Section 3",
          content:
            "<p>Sed elementum sapien ut sapien imperdiet, eu venenatis enim rhoncus. Praesent euismod tincidunt rhoncus. Duis cras amet:</p><ul><li>List item one</li><li>List item two</li><li>List item three</li></ul>",
        },
        {
          title: "Section 4",
          content:
            "<p>Cras dictum. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Aenean lacinia mauris vel est.</p><p>Suspendisse eu nisl. Nullam ut libero. Integer dignissim consequat lectus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.</p>",
        },
      ],
      currentContent: "",
      currentIndex: 0,
    };
  },
  mounted() {
    console.log(this.dataLists[0].content);
    this.currentContent = this.dataLists[0].content
  },
  methods: {
    getContent: function (index) {
      this.currentContent = this.dataLists[index].content;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.row-margin-05 {
  margin-right: 0.5em;
}
.row-margin-10 {
  margin-right: 1em;
}
.row-margin-20 {
  margin-right: 2em;
}
.row-margin-30 {
  margin-right: 3em;
}
</style>
