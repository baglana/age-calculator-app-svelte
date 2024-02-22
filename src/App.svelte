<script lang="ts">
    let dobDay: number;
    let dobMonth: number;
    let dobYear: number;

    $: dob = new Date(dobYear, dobMonth - 1, dobDay);
    $: years = new Date(Date.now() - dob.getTime()).getUTCFullYear() - 1970;
    $: months = new Date(Date.now() - dob.getTime()).getMonth();
    $: days = new Date(Date.now() - dob.getTime()).getDate();
</script>

<main>
    <form>
        <label for="day">
            DAY
            <input bind:value={dobDay} name="day" type="number">
        </label>
        <label for="month">
            MONTH
            <input bind:value={dobMonth} name="month" type="number">
        </label>
        <label for="year">
            YEAR
            <input bind:value={dobYear} name="year" type="number">
        </label>

        <output>
            {#if years}
                <p>{years} years</p>
            {/if}
            {#if months}
                <p>{months} months</p>
            {/if}
            {#if days}
                <p>{days} days</p>
            {/if}
        </output>
    </form>
</main>