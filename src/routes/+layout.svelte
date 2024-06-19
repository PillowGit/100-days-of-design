<div class="page-holder">
  <div class="page-content">
    <slot />
  </div>
</div>

<style>
  .page-holder {
    width: 100%;
    min-height: 50%;
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .page-content {
    width: 100%;
    max-width: 65rem;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
