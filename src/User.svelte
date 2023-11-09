<script>
  export let user;
</script>

<div class="user-component-wrapper">
  <img width="100px" src={user.picture.large} alt="thumbnail"/>
  <p>Name: {user.name.first}</p>
  <p>Postcode: {user.location.postcode}</p>
  <p>Coordinates: [lat: {user.location.coordinates.latitude}, long: {user.location.coordinates.longitude}]</p>
  <p>Email: {user.email}</p>
  <p>City: {user.location.city}</p>
</div>

<style>

  img {
    margin: 3px;
  }

  .user-component-wrapper {
    height: 600px;
    text-align: center;
    margin: 5px;
    width: 250px;
    border: 1px solid black;
    border-radius: 10px;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
  
</style>
