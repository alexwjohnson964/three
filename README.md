# three
import * as THREE from "https://esm.sh/three";
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
const renderer = new THREE.WebGLRenderer();
renderer.setSize( window.innerWidth, window.innerHeight );
document.body.appendChild( renderer.domElement );

const geometry = new THREE.BoxGeometry( 1, 1, 1 );
const material = new THREE.MeshBasicMaterial( { color: 'red' } );
const cube = new THREE.Mesh( geometry, material );
console.log(cube)
scene.add( cube );

const lmaterial = new THREE.LineBasicMaterial( { color: 0x0000ff } );
const points = [];
points.push( new THREE.Vector3( 0, 0, -5 ) );
points.push( new THREE.Vector3( 0, 5, -5 ) );
points.push( new THREE.Vector3( 10, 0, -5 ) );

const lgeometry = new THREE.BufferGeometry().setFromPoints( points );
const line = new THREE.Line( lgeometry, lmaterial );
scene.add( line );

camera.position.z = 5;

function animate() {
	renderer.render( scene, camera );
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;
}
renderer.setAnimationLoop( animate );
