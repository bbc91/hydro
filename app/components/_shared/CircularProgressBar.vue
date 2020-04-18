<template>
    <GridLayout :height="height" :width="height">
        <RadRadialGauge>
            <RadialScale
                v-tkRadialGaugeScales
                startAngle="180"
                sweepAngle="180"
            >
                <ScaleStyle
                    v-tkRadialScaleStyle
                    ticksVisible="false"
                    labelsVisible="false"
                    lineThickness="0"
                >
                </ScaleStyle>

                <RadialBarIndicator
                    v-tkRadialScaleIndicators
                    minimum="0"
                    maximum="100"
                >
                    <BarIndicatorStyle
                        v-tkRadialBarIndicatorStyle
                        :fillColor="fillBackgroundColor"
                        cap="Round"
                        barWidth="0.05"
                    >
                    </BarIndicatorStyle>
                </RadialBarIndicator>

                <RadialBarIndicator
                    v-tkRadialScaleIndicators
                    minimum="0"
                    :maximum="value"
                    isAnimated="true"
                >
                    <BarIndicatorStyle
                        v-tkRadialBarIndicatorStyle
                        :fillColor="fillColor"
                        cap="Round"
                        barWidth="0.05"
                    >
                    </BarIndicatorStyle>
                </RadialBarIndicator>
            </RadialScale>
        </RadRadialGauge>
    </GridLayout>
</template>

<script>
export default {
    props: {
        size: { default: 100 },
        progress: { default: 0 },
        offset: { default: 0 },
        textColor: { default: "#bfbfc4" },
        fillColor: { default: "#4aa9ee" },
        fillBackgroundColor: { default: "#efeff4" },
    },
    computed: {
        height() {
            return Math.min(this.size, 450);
        },
        value() {
            return Math.min(this.progress, 100);
        },
    },
};
</script>

<style></style>
