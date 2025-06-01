<template>
    <li>
        <h2>{{ friendName }} {{ friendSurname }} {{ isFavorite ? '(Favourite)' : ''}}</h2>
        <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
        <button @click="toggleFavorite">{{ friendIsFavorite ? 'Unfavorite' : 'Favorite' }} </button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone:</strong> {{ phoneNumber }}</li>
            <li><strong>Email:</strong> {{ emailAddress }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    props: {
        id: {
            type: String,
            required: true
        },
        friendName: {
            type: String,
            required: true
        },
        friendSurname: {
            type: String,
            required: true
        },
        phoneNumber: {
            type: String,
            required: true
        }, 
        emailAddress: {
            type: String,
            required: true
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false
        }
    },
    emits: {
        'toggle-favorite': function(id) {
            if (id) {
                return true;
            } else {
                console.warn('Id is missing!');
            }
        }
    },
    data() {
        return {
            detailsAreVisible: false,
        }
    },
    methods: {
        toggleDetails() {
			this.detailsAreVisible = !this.detailsAreVisible;
		},
        toggleFavorite() {
            this.friendIsFavorite = !this.friendIsFavorite;
            this.$emit('toggle-favorite', this.id);
        }
    }
}
</script>