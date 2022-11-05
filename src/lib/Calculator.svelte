<script>
	const pointCost = [0, 0, 0, -9, -6, -4, -2, -1, 0, 1, 2, 3, 4, 5, 7, 9, 12, 15, 19]
	const pointsAllowed = 27
	const minScore = 3
	const maxScore = 18

	let pointsRemaining = pointsAllowed
	let stats = [8,8,8,8,8,8]

	function incStr() {
	  incrStat(0)
	}
	function decStr() {
	  decStat(0)
	}
	function incDex() {
	  incrStat(1)
	}
	function decDex() {
	  decStat(1)
	}
	function incCon() {
	  incrStat(2)
	}
	function decCon() {
	  decStat(2)
	}
	function incWis() {
	  incrStat(3)
	}
	function decWis() {
	  decStat(3)
	}
	function incInt() {
	  incrStat(4)
	}
	function decInt() {
	  decStat(4)
	}
	function incChr() {
	  incrStat(5)
	}
	function decChr() {
	  decStat(5)
	}

	function incrStat(idx) { 
		let stat = stats[idx]
		if(stat !== maxScore) {
			stats[idx] = stat + 1
			recalcPointsAllowed()
		}
	}
	function decStat(idx) { 
		let stat = stats[idx]
		if(stat !== minScore) {
			stats[idx] = stat - 1
			recalcPointsAllowed()
		}
	}

	function recalcPointsAllowed() {
		let pointsTaken = stats.reduce((total, stat) => {
			let cost = pointCost[stat]
			return total + cost
		}, 0)
		pointsRemaining = pointsAllowed - pointsTaken
	}
</script>

<style>
  .my-stat {
	display: inline-block;
	width: 150px;
	text-align: left;
  }
  .point-header {
	width: 150px;
	display: inline-block;
	text-align: left;
  }
</style>

<h4>
	<div class="point-header">Points Allowed</div> {pointsAllowed}
</h4>
<h4 class="point-headers">
	<div class="point-header">Points Remaining</div> {pointsRemaining}
</h4>

<div>
	<div class="my-stat">Strength:</div> <span>{stats[0]}</span> <button on:click={incStr}>Add</button> <button on:click={decStr}>Remove</button>
</div>
<div>
	<div class="my-stat">Dexterity:</div>  <span>{stats[1]}</span><button on:click={incDex}>Add</button> <button on:click={decDex}>Remove</button>
</div>
<div>
	<div class="my-stat">Constitution:</div> <span>{stats[2]}</span> <button on:click={incCon}>Add</button> <button on:click={decCon}>Remove</button>
</div>
<div>
	<div class="my-stat">Wisdom:</div> <span>{stats[3]}</span> <button on:click={incWis}>Add</button> <button on:click={decWis}>Remove</button>
</div>
<div>
	<div class="my-stat">Intelligence:</div> <span>{stats[4]}</span> <button on:click={incInt}>Add</button> <button on:click={decInt}>Remove</button>
</div>
<div>
	<div class="my-stat">Charisma:</div> <span>{stats[5]}</span> <button on:click={incChr}>Add</button> <button on:click={decChr}>Remove</button>
</div>