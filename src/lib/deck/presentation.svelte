<script lang="ts">
  import Slide from "../components/slide.svelte";
  import SingleCenter from "../components/singleCenter.svelte";
  import Code from "../components/code.svelte";
</script>


<Slide animate>
  <h1>What is a <span class="text-blue-500">container?</span></h1>
  <p class="fragment">"A container is a standard unit of software"</p>
  <p class="fragment">"A container is an isolated environment for your code"</p>
  <p class="fragment">"Containers are similar to VMs, [...]"</p>
</Slide>

<Slide animate>
  <SingleCenter>
    🤨
  </SingleCenter>

  <aside class="notes">
    Alles nicht wirklich hilfreich.
    => Schauen wir uns mal an, woraus ein Container aufgebaut ist.
  </aside>
</Slide>


<Slide>
  <Slide animate>
    <p data-id="text">"A container is an abstraction over multiple different technologies offered by the Linux
      kernel."</p>
    <div class="r-hstack gap-5" data-id="kernel-feature-boxes">
      <div class="bg-red-400 p-5 rounded" data-id="box-1">Control Groups</div>
      <div class="bg-blue-400 p-5 rounded" data-id="box-2">Namespaces</div>
      <div class="bg-green-400 p-5 rounded" data-id="box-3">Filesystems</div>
    </div>
  </Slide>

  <Slide animate>

    <div class="r-hstack gap-5" data-id="kernel-feature-boxes">
      <div class="bg-red-400 p-5 rounded" data-id="box-1">Control Groups</div>
      <div class="bg-blue-400 p-5 rounded" data-id="box-2">Namespaces</div>
      <div class="bg-gray-400 p-5 rounded" data-id="box-3">Filesystems</div>
    </div>

    <div class="r-stretch mt-5" data-id="text">

      <p>limit resources containers use</p>
      <p>control resource visibility</p>
      <p>make it appear that container has its own, isolated copy of a resource</p>

    </div>

  </Slide>

  <Slide animate>

    <div class="r-hstack gap-5" data-id="kernel-feature-boxes">
      <div class="bg-gray-400 p-5 rounded" data-id="box-1">Control Groups</div>
      <div class="bg-gray-400 p-5 rounded" data-id="box-2">Namespaces</div>
      <div class="bg-green-400 p-5 rounded" data-id="box-3">Filesystems</div>
    </div>

    <div class="r-stretch mt-5" data-id="text">
      <p>enable layered architecture of container images</p>
    </div>

  </Slide>
</Slide>

<Slide animate>

  <h1 class="text-xl uppercase">A container is <span class="text-red-500">not</span> a VM!</h1>
  <p class="fragment fade-up fade-in-then-semi-out">There is no virtualization or emulation involved.</p>
  <p class="fragment fade-up fade-in-then-semi-out">Processes in a container are processes on the host.</p>
  <p class="fragment fade-up fade-in-then-semi-out">Their access to certain resources is controlled.</p>
  <p class="fragment fade-up fade-in">They can see a well-defined part of the host system/other
    processes/resources.</p>

</Slide>

<Slide animate>

  <h1 class="text-xl uppercase">A container is <span class="text-red-500">not</span> a VM!</h1>
  <img alt="VMs vs Containers" class="" src="vms-vs-containers.png">

</Slide>

<Slide
  animate
  data-background-image="runtimes.png"
  data-background-size="contain"
>
  <div class="flex flex-col items-center justify-center">

    <h1 class="w-1/2 h-1/2 bg-[#191919] bg-opacity-80" data-id="heading-runtime">Containers are run by <span
      class="text-blue-500">runtimes</span>.
    </h1>

    <div class="bg-[#191919] bg-opacity-80 fragment ">
      <p class="fragment">Different runtimes have different features and priorities.</p>
      <p class="fragment">They all implement the OCI Runtime Specification.</p>
    </div>


  </div>
</Slide>

<Slide animate>
  <h1>What is Docker?</h1>

</Slide>

<Slide
  animate
>
  <h1>What is Docker?</h1>
  <div class="flex">
    <div>
      <p>Not a runtime!</p>
      <p class="fragment fade-in-then-semi-out">platform for developing, shipping, and running applications in
        containers</p>
      <p class="fragment fade-in-then-semi-out">consists of multiple components, one of those components is a
        container
        runtime (runc)
      </p>

    </div>
    <img alt="Docker Architecture" class=" w-1/2 h-auto" src="docker-architecture.png">
  </div>
</Slide>

<Slide
  animate
>
  <h1>What is Docker?</h1>
  <div class="flex">
    <img alt="Docker Architecture" class="w-1/2 h-auto" src="docker-architecture.png">
    <div>
      <p class="fragment fade-in-then-semi-out">The <span class="text-blue-400">docker engine</span> accepts user
        commands,
        downloads/uploads
        images, etc.
      </p>
      <p class="fragment fade-in-then-semi-out"><span class="text-blue-400">containerd</span> manages images,
        storage,
        network
        attachment, etc.
      </p>
      <p class="fragment fade-in-then-semi-out"><span class="text-blue-400">runc</span> spawns and runs containers
        by
        using kernel functionality.
      </p>
    </div>
  </div>
</Slide>

<Slide>
  <SingleCenter>
    🏃🏼❔
  </SingleCenter>
</Slide>

<Slide animate>
  <h1>Images and how to create and run them</h1>
  <h2 class="text-left">An image is a...</h2>
  <ul>
    <li class="fragment fade-in-then-semi-out list-none">...set of files that make up the "userland" inside a
      container
    </li>
    <li class="fragment fade-in-then-semi-out list-none">... description of the installed state of a system</li>
    <li class="fragment fade-in-then-semi-out list-none">... "snapshot of a container"</li>
    <li class="fragment fade-in-then-semi-out list-none">... "fancy zip or tar archive"</li>
  </ul>
</Slide>

<Slide animate>
  <h1>Images and how to create and run them</h1>
  <div class="w-1/2 mx-auto ">
    <Code class="text-sm" iconType="file" description="Directory" language="console">
      {`
    my_fancy_app/
    ├── Dockerfile
    └── app.py
    `}
    </Code>
  </div>
</Slide>

<Slide animate>
  <h1>Images and how to create and run them</h1>
  <div class="w-1/2 mx-auto ">
    <Code class="text-sm" description="Directory" language="console" iconType="file">
      {`
    my_fancy_app/
    ├── Dockerfile
    └── app.py
    `}
    </Code>
  </div>
  <p class="text-xl">A Dockerfile contains all commands necessary to build an image</p>
  <div class="fragment grid grid-cols-2">
    <Code class="text-lg" description="Dockerfile" iconType="docker" language="dockerfile">
      {`
      FROM ubuntu:23.04
      RUN apt update &&
          apt install -y python3
      COPY . /app
      CMD ["python3", "/app/app.py"]
      EXPOSE 3000
    `}
    </Code>
    <div class="text-lg  inline-flex flex-col justify-center">
      <span>Build on top of base image</span>
      <hr class="w-60 mx-auto border-1 ">
      <span>Install dependencies</span>
      <br>
      <hr class="w-60 mx-auto border-1 ">
      <span>copy all files of current directory to /app in the container</span>
      <hr class="w-60 mx-auto border-1 ">
      <span>run the app inside the container</span>
      <hr class="w-60 mx-auto border-1 ">
      <span>mark port 3000 as exposed</span>
    </div>
  </div>
  <p></p>
</Slide>

<Slide animate>
  <h1>Images and how to create and run them</h1>
  <Code description="Shell" iconType="console" id="minimal-docker-example" language="console" lineNumbers
        style="overflow-y: hidden">
    {`
    # build a named image from the Dockerfile
    $ docker build -t my_fancy_app .
    `}
  </Code>
</Slide>

<Slide animate>
  <h1>Images and how to create and run them</h1>
  <Code class="overflow-x-hidden" description="Shell" iconType="console" id="minimal-docker-example"
        language="console" lineNumbers
        style="overflow-y: hidden">
    {`
    # build a named image from the Dockerfile
    $ docker build -t my_fancy_app .
    # create and run a container using the built image
    # expose a port from the container to the host
    $ docker container run -p 3000:3000 my_fancy_app
    `}
  </Code>
</Slide>

<Slide animate data-background-color="#2191FB">
  <div class="flex justify-center">
    <img alt="monkey_typing" class="w-1/2 h-auto" src="https://media.giphy.com/media/zOvBKUUEERdNm/giphy.gif">
  </div>
</Slide>

<Slide animate data-background-color="#2191FB">
  <div class="flex justify-center">
    <img alt="monkey_typing" class="w-1/3 h-auto" src="https://media.giphy.com/media/zOvBKUUEERdNm/giphy.gif">
  </div>
  <h1>Exercise 1: Build images and run containers</h1>

</Slide>

<Slide animate data-background-color="#2191FB">
  <h1>Exercise 1: Build images and run containers</h1>
  <p>🗒️ 7 small tasks</p>
  <p>⌛ ca. 15 minutes</p>
</Slide>


<Slide animate restart>
  <h1>Changing the html page had no effect. Why is that?</h1>

  <aside class="notes">
    Fragestellung: Kann sich jemand noch daran erinnern, was ich vorhin über Images gesagt habe?
  </aside>
</Slide>


<Slide animate>
  <h1>Changing the html page had no effect. Why is that?</h1>
  <p>Our code got "baked" into the image when building it.</p>
  <p class="fragment">
    When we created and ran the container, it operated with its own copy of our code.
  <p />
  <p class="fragment">Naturally, changing the original has no effect on the container's copy at all.</p>
</Slide>

<Slide animate restart>
  <h1>Bind Mounts and Volumes</h1>
  <p>Used to share (mount) a directory from the host system into the container.</p>
  <p>As such, the container "sees" all file changes instantly when saving the file.</p>
</Slide>

<Slide animate>
  <h1>Bind Mounts</h1>
  <Code description="Shell" iconType="console" language="console">
    {`
    # mount the current directory into the container at /app
    # and start a bash session in the container root
    $ docker container run -it \\
      --mount type=bind,src="$(pwd)",target=/app my_fancy_app
    `}
  </Code>
</Slide>

<Slide animate data-background-color="#A0C1B9">
  <div class="flex justify-center">
    <img alt="monkey_typing" class="w-1/2 h-auto"
         src="https://i.chzbgr.com/full/8270686464/h7779056E/coding-is-an-art">
  </div>
</Slide>

<Slide animate data-background-color="#A0C1B9">
  <div class="flex justify-center">
    <img alt="monkey_typing" class="w-1/2 h-auto"
         src="https://i.chzbgr.com/full/8270686464/h7779056E/coding-is-an-art">
  </div>
  <h1>Exercise 2: Bind Mounts</h1>
  <p class="fragment">🗒️ 2 sections</p>
  <p class="fragment">⌛ ca. 15 minutes</p>
</Slide>


<Slide animate restart>
  <h1>Problems with the current approach to specify containers</h1>
  <p class="text-red-300 text-2xl">Every time we need to run a container, we have to build ourselves a shell
    command.</p>
  <p class="text-red-300 text-2xl">Depending on the desired environment, the shell command can get very long.</p>
  <p class="text-red-300 text-2xl">Typing out long shell commands is error prone.</p>
</Slide>

<Slide animate
       data-background-image="https://media0.giphy.com/media/3oKHWnGeVGBpC981DW/giphy.gif?cid=ecf05e47r9x8sfmkcr7o5xubzemflq0q1n3kxt5yxtojtwsp&ep=v1_gifs_related&rid=giphy.gif&ct=g">
  <p class="text-red-300 text-2xl">Every time we need to run a container, we have to build ourselves a shell
    command.</p>
  <p class="text-red-300 text-2xl">Depending on the desired environment, the shell command can get very long.</p>
  <p class="text-red-300 text-2xl">Typing out long shell commands is error prone.</p>

  <Code description="Shell" iconType="console" language="console">
    {`
        # frontend container
        $ docker run \\
          -d \\
          --name frontend-app \\
          -p 80:80 \\
          --network my-network \\
          -e NODE_ENV=production \\
          -e API_URL=http://backend-app:3000/api \\
          -v /path/on/host/frontend:/app \\
          your-frontend-image:latest && \\

        # backend container
        $ docker run \\
          -d \\
          --name backend-app \\
          --network my-network \\
          -e NODE_ENV=production \\
          -e DATABASE_URL=mysql://user:password@db-host/db-name \\
          -v /path/on/host/backend:/app \\
          your-backend-image:latest && \\

        # backend db
        $ docker run \\
          -d \\
          --name database \\
          --network my-network \\
          -e MYSQL_ROOT_PASSWORD=root-password \\
          -e MYSQL_DATABASE=db-name \\
          your-database-image:latest

        `}
  </Code>
</Slide>

<Slide>
  <h1>So, what would a good (linux) developer do to automate those long commands?</h1>
  <p class="text-sm">If you know what I'm getting at, hold it for a minute...</p>
</Slide>

<Slide animate data-background-color="white" data-background-transition="fade"
       data-transition="zoom" data-transition-speed="fast">
  <div>
    <img alt="bash_logo" data-id="bash_logo" src="bash_logo.png" />
  </div>
</Slide>

<Slide animate>
  <img alt="bash_logo" data-id="bash_logo" height="auto" src="bash_logo_white.png" style="margin: 0 auto"
       width="50%" />
  <p>In the early years of docker, developers would create bash (batch on windows) scripts to reuse docker run
    commands.</p>
  <p>Docker, Inc quickly saw this need for automation and reuse and created... </p>
</Slide>

<Slide animate>
  <h1>Docker Compose</h1>
</Slide>

<Slide animate>
  <h1>Docker Compose</h1>

  <p class="text-2xl">provides a declarative way to describe the needed (multi-) container configuration</p>
  <p class="text-2xl">with a single command, all configured services get created and started from the
    configuration</p>


  <p class="text-red-300" data-id="this_becomes_this">This...</p>
  <Code class="text-lg" description="Shell" iconType="console">
    {`
            $ docker container run \\
               --rm \\
               -it \\
               -p:3000:3000 \\
               --mount type=bind,src="$(pwd)",target=/app \\
               --mount type=volume,src="node_modules",target=/app/node_modules/ \\
               task02:dev \\
               npm run start:dev
            `}
  </Code>

</Slide>

<Slide animate>
  <h1>Docker Compose</h1>
  <p class="text-2xl">provides a declarative way to describe the needed (multi-) container configuration</p>
  <p class="text-2xl">with a single command, all configured services get created and started from the
    configuration</p>

  <p class="text-green-300" data-id="this_becomes_this">...becomes this.</p>

  <span class="fiv-viv fiv-icon-yml"></span>
  <Code class="text-lg" description="docker-compose.yml" iconType="docker" language="yaml">
    {`
           version: '3'
            services:
              node_server:
                image: task02:dev
                volumes:
                  - ./:/app
                  - /app/node_modules
                ports:
                  - "3000:3000"
                command: npm run start:dev
            `}
  </Code>

</Slide>

<Slide animate>
  <Code class="text-lg" description="docker-compose.yml" iconType="docker" language="yaml">
    {`
           version: '3'
            services:
              node_server:
                image: task02:dev
                volumes:
                  - ./:/app
                  - /app/node_modules
                ports:
                  - "3000:3000"
                command: npm run start:dev
            `}
  </Code>
  <p>A YAML file containing all necessary configuration on how all needed containers should be started.</p>
</Slide>

<Slide animate>
  <h2>Benefits of using a file instead of a command:</h2>
  <p class="text-xl">Readability</p>
  <p class="text-xl">A file can be shared with others and put under
    <span class="text-2xl underline bold italic">version control</span>
  </p>
  <p class="text-xl">Different environments can use different configuration files</p>
  <p class="text-xl">IDEs can check the syntax and provide auto-completion while creating it</p>

</Slide>

<Slide animate>
  <h2>Benefits of using docker compose:</h2>
  <p class="text-xl">Scalability</p>
  <p class="text-xl">Portability</p>
  <p class="text-xl">Dependency Management</p>
  <p class="text-xl">Networking</p>
  <p class="text-xl">... a million more</p>
</Slide>

<Slide animate data-background-color="#F9B9F2">
  <SingleCenter>
    <img
      alt="Chris Pratt"
      src="https://media3.giphy.com/media/S9i8jJxTvAKVHVMvvW/giphy.gif?cid=ecf05e477x8tobhle98crnagohjh8mc54f8wlwtmykb7c5nz&ep=v1_gifs_search&rid=giphy.gif&ct=g">
  </SingleCenter>
  <h1>Showcase: Docker Compose</h1>
  <p>⌛ ???</p>
</Slide>


<Slide data-background-color="#AEF78E">
  <div class="flex flex-col min-h-[90vh]">

    <h1>{`</>`}</h1>
    <div class="flex h-full flex-1 flex-col justify-center">
      <p>Thanks for listening.</p>
      <p>Thanks for participating.</p>
      <p>Never use <code>:latest</code>!</p>
    </div>

    <div class="text-sm">Made with
      <a href="https://revealjs.com/">reveal.js</a>,
      <a href="https://svelte.dev/">Svelte</a>,
      <a href="https://tailwindcss.com/">tailwindcss</a>
      and ❤️ by Henry Germany
    </div>

  </div>

</Slide>