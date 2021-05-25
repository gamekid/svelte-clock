<script lang="ts">
	let hourTens: number = null;
  let hourOnes: number = null;
  let minuteTens: number = null;
  let minuteOnes: number = null;
  updateTime();
  setInterval(() => updateTime(), 10000)

  function updateTime() {
    let d = new Date();
    
    [hourTens, hourOnes] = d
      .getHours()
      .toString()
      .padStart(2, '0')
      .split('')
      .map(Number);

    [minuteTens, minuteOnes] = d
      .getHours()
      .toString()
      .padStart(2, '0')
      .split('')
      .map(Number);
  }

</script>

<div class="clock">
  <div class="digit hour-tens">{hourTens}</div>
  <div class="digit hour-ones">{hourOnes}</div>
  <div class="colon">:</div>
  <div class="digit minute-tens">{minuteTens}</div>
  <div class="digit minute-ones">{minuteOnes}</div>
</div>

<style>
	.clock {
    position: relative;
    display: inline-block;

    color: var(--neon-color);
    font-family: 'Courier Prime', monospace;
    
    border: .5em solid var(--neon-color);
    border-radius: .75em;

    text-shadow:
      0 0 0.25em hsl(0 0% 100% / 0.3)
    ;

    box-shadow: 
      inset 0 0 2em 0 var(--neon-color),
      0 0 2em 0 var(--neon-color)
    ;

    perspective: 4em;
	}

  .clock::before {
    content: "";
    position: absolute;
    background: var(--neon-color);
    top: 100%;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;

    transform: 
      rotateX(40deg)
      scale(1, 0.35)
    ;
    filter: blur(4em);
    opacity: 0.7;
  }

  .clock > * {
    display: inline-block;
    font-size: 6em;
  }
  .clock > *:first-child {
    padding-left: .167em;
  }
  .clock > *:last-child {
    padding-right: .167em;
  }

  .digit {
    position: relative;
  }

  .digit::before {
    pointer-events: none;
    content: "";
    position: absolute;
    background: var(--neon-color);
    top: 120%;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;

    transform:
      rotateX(40deg)
      scale(1, 0.3)
    ;
    filter: blur(.25em);
    opacity: 0.0;
  }

  .digit:hover {
    background: var(--neon-color);
    color: black;

    text-shadow: none;
  }

  .digit:hover::before {
    opacity: .5;
  }

</style>