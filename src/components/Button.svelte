<style>
  div {
    display: block;
    height: 42px;
  }

  button {
    width: 100%;
    height: 100%;
    background-color: #ff3e00;
    color: #fff;
    border: 0px solid transparent;
    cursor: pointer;
    box-sizing: border-box;
    transition: all 512ms ease;
    text-transform: uppercase;
    font-weight: 100;
  }

  button:hover {
    background-color: #fff;
    color: #ff3e00;
    border: 4px solid;
    font-weight: 500;
  }
</style>

<div>
  <button on:click>
    <slot>
      Action
    </slot>
  </button>
</div>