<script>
  import * as THREE from 'three';
  import { onMount } from 'svelte';

  let renderer, scene, camera, mesh;

  function init() {
    // create renderer
    renderer = new THREE.WebGLRenderer();
    renderer.setSize( window.innerWidth, window.innerHeight );
    document.querySelector('#container').appendChild( renderer.domElement );

    // create scene
    scene = new THREE.Scene();

    // create camera
    camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
    camera.position.z = 5;

    // create mesh
    const geometry = new THREE.BoxGeometry();
    const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
    mesh = new THREE.Mesh( geometry, material );
    scene.add( mesh );
  }

  function animate() {
    requestAnimationFrame( animate );

    mesh.rotation.x += 0.01;
    mesh.rotation.y += 0.02;

    renderer.render( scene, camera );
  }

  onMount(() => {
    init();
    animate();
  });
</script>

<style>
  #container {
    width: 100%;
    height: 100%;
  }
</style>

<div id="container"></div>