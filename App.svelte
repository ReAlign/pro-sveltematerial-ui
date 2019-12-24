<svelte:head>
  <title>Dialogs - SMUI</title>
</svelte:head>

<section>
  <h2>Dialogs</h2>

  <div>
    <Dialog
      bind:this={simpleDialog}
      aria-labelledby="simple-title"
      aria-describedby="simple-content">
      <!-- Title cannot contain leading whitespace due to mdc-typography-baseline-top() -->
      <Title id="simple-title">Dialog Title</Title>
      <Content id="simple-content">
        Super awesome dialog body text?
      </Content>
      <Actions>
        <Button on:click={() => clicked = 'No'}>
          <Label>No</Label>
        </Button>
        <Button on:click={() => clicked = 'Yes'}>
          <Label>Yes</Label>
        </Button>
      </Actions>
    </Dialog>

    <Button on:click={() => simpleDialog.open()}>
      <Label>Open Dialog</Label>
    </Button>
  </div>

  <pre class="status">Clicked: {clicked}</pre>
</section>

<script>
  import Dialog, {Title, Content, Actions, InitialFocus} from '@smui/dialog';
  import Button, {Label} from '@smui/button';

  let simpleDialog;

  let clicked = 'Nothing yet.';
  let response = 'Nothing yet.';

  let volumeMedia = 100;
  let volumeRingtone = 80;
  let volumeAlarm = 80;
  function closeHandler(e) {
    switch (e.detail.action) {
      case 'none':
        response = 'Ok, well, you\'re wrong.';
        break;
      case 'all':
        response = 'You are correct. All dogs are the best dog.';
        break;
      default:
        response = 'It\'s a simple question. You should be able to answer it.';
        break;
    }
  }
  function selectionCloseHandler(e) {
    if (e.detail.action === 'accept') {
      selected = selection;
    }
    selection = 'Radishes';
  }
</script>