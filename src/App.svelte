<script lang="ts">
    import citations from '/combined_data.json';

    class Citation {
        constructor(type: string, text: string, ts: number, user_profile: UserProfile) {
            this.type = type;
            this.text = text;
            this.ts = ts;
            this.user_profile = user_profile;
        }
        text: string;
        type: string;
        ts: number;
        user_profile: {
            image_72: string;
            first_name: string,
            real_name: string,
            display_name: string,
        }
    }
    type UserProfile = {
        image_72: string;
        first_name: string,
        real_name: string,
        display_name: string,
    }

    function formatCitation(citation) {
        return new Citation(citation.type, citation.text, citation.ts, citation.user_profile)
    }
</script>
<main>
    {#each citations as citation}
        <div>
            {formatCitation(citation).text}
        </div>
    {/each}
</main>
<style>
    main {
        display: flex;
        flex-direction: column;
    }
</style>
