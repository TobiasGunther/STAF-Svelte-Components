<script lang="ts">
    import { Card, CardBody } from '@statsforvalteren/staf-komponentbibliotek-svelte';
    const cardProps = {
    title: "This is a title"
    }
</script>

<Card>
    <CardBody {...cardProps}>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s.</CardBody>
</Card>