<template>
    <GridLayout rows="*, 300" columns="*">
        <CircularProgressBar
            row="0"
            rowSpan="0"
            col="0"
            :size="320"
            :progress="goalProgress"
        />
        <StackLayout
            background="white"
            androidElevation="8"
            marginTop="0"
            borderRadius="999"
            width="265"
            height="265"
            row="0"
            col="0"
        >
            <StackLayout class="goalBlock">
                <Label class="goalText" text="Цел" />
                <Label
                    class="intakeIndicatorLabel"
                    :text="currentWater + ' / ' + waterGoal + ' мл'"
                />
                <Label width="100%" @tap="takeWater()" class="drinkButton">
                    <Span class="fal" text.decode="&#xf804;" fontSize="30"></Span>
                    <Span class="fal" text.decode=" &#xf067;"></Span>
                </Label>
                <Label width="100%" @tap="removeWater()" class="drinkButton">
                    <Span class="fal" text.decode="&#xf804;" fontSize="30"></Span>
                    <Span class="fal" text.decode=" &#xf068;"></Span>
                </Label>
            </StackLayout>
        </StackLayout>
    </GridLayout>
</template>

<script>
import CircularProgressBar from "./_shared/CircularProgressBar";
export default {
    components: {
        CircularProgressBar,
    },
    data() {
        return {
            waterGoal: 1200,
            currentWater: 0,
        };
    },
    computed: {
        goalProgress: function() {
            return (this.currentWater * 100) / this.waterGoal;
        },
    },
    methods: {
        takeWater() {
            if (this.currentWater + 200 >= this.waterGoal) {
                this.currentWater = this.waterGoal;
            } else {
                this.currentWater = this.currentWater + 200;
            }
        },
        removeWater() {
            if (this.currentWater - 200 <= 0) {
                this.currentWater = 0;
            } else {
                this.currentWater = this.currentWater - 200;
            }
        },
    },
};
</script>

<style scoped>
.intakeIndicatorLabel {
    width: 100%;
    text-align: center;
    color: #666;
    font-size: 25;
    margin-bottom: 10;
}

.goalBlock {
    margin-top: 60;
    margin-bottom: 15;
}

.goalText {
    margin-bottom: 15;
    color: #4aa9ee;
    font-size: 20;
    width: 100%;
    text-align: center;
}

.drinkButton {
    width: 100%;
    text-align: center;
    padding-top: 10;
    padding-bottom: 10;
}
</style>
