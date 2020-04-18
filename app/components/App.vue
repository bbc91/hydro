<template>
    <Page actionBarHidden="true">
        <TabView
            android:tabBackgroundColor="#4aa9ee"
            android:tabTextColor="#ffffff"
            android:selectedTabTextColor="#ffffff"
            androidSelectedTabHighlightColor="#ffffff"
        >
            <TabViewItem class="fal menuButton" title.decode="&#xf043; Вода">
                <GridLayout rows="*, 300" columns="*">
                    <CircularProgressBar
                        row="0"
                        rowSpan="0"
                        col="0"
                        :size="300"
                        :progress="goalProgress"
                    />
                    <StackLayout
                        background="grey"
                        marginTop="0"
                        borderRadius="999"
                        width="265"
                        height="265"
                        row="0"
                        col="0"
                        >.
                        <Label
                            class="intakeIndicatorLabel"
                            :text="currentWater + ' / ' + waterGoal + ' мл'"
                        />
                        <Button width="100" text="Пийни" @tap="takeWater()" />
                        <Button
                            width="100"
                            text="Плювни"
                            @tap="removeWater()"
                        />
                    </StackLayout>
                </GridLayout>
            </TabViewItem>
            <TabViewItem class="fal menuButton" title.decode="&#xf1da; История">
                <GridLayout columns="*" rows="*">
                    <Label
                        class="message"
                        text="Tab 2 Content"
                        col="0"
                        row="0"
                    />
                </GridLayout>
            </TabViewItem>
            <TabViewItem
                class="fal menuButton"
                title.decode="&#xf013; Настройки"
            >
                <GridLayout columns="*" rows="*">
                    <Label
                        class="message"
                        text="Tab 3 Content"
                        col="0"
                        row="0"
                    />
                </GridLayout>
            </TabViewItem>
        </TabView>
    </Page>
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
    color: #fff;
    margin-top: 100;
    margin-bottom: 15;
    font-size: 25;
}
</style>
