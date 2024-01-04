<script lang="ts">
  import Slide from "./slide.svelte";
  import SingleCenter from "./singleCenter.svelte";
  import Code from "./code.svelte";
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
      <p class="fragment fade-in-then-semi-out">consists of multiple components, one of those components is a container
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
      <p class="fragment fade-in-then-semi-out"><span class="text-blue-400">containerd</span> manages images, storage,
        network
        attachment, etc.
      </p>
      <p class="fragment fade-in-then-semi-out"><span class="text-blue-400">runc</span> spawns and runs containers by
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
  <pre class="bg-white text-black">
    my_fancy_app/
    ├── Dockerfile
    └── app.py
    </pre>
  </div>
</Slide>

<Slide animate>
  <h1>Images and how to create and run them</h1>
  <Code>
    {`
    my_fancy_app/
    ├── Dockerfile
    └── app.py
    `}
  </Code>
  <p>A Dockerfile contains all commands necessary to build an image</p>
  <div class="fragment grid grid-cols-2">
    <Code>
      {`
      FROM ubuntu:23.04
      RUN apt update &&
          apt install -y python3
      COPY . /app
      CMD ["python3", "/app/app.py"]
      EXPOSE 3000
    `}
    </Code>
    <div class="text-xl inline-flex flex-col justify-center">
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
  <Code id="minimal-docker-example" lineNumbers>
    {`
    # build a named image from the Dockerfile
    $ docker buildx build -t my_fancy_app .
    `}
  </Code>
</Slide>

<Slide animate>
  <h1>Images and how to create and run them</h1>
  <Code id="minimal-docker-example" lineNumbers>
    {`
    # build a named image from the Dockerfile
    $ docker buildx build -t my_fancy_app .
    # create and run a container using the built image
    # expose a port from the container to the host
    $ docker run -p 3000:3000 my_fancy_app
    `}
  </Code>
</Slide>
