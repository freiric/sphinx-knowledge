Open Telemnetry
=====================

spring-boot-autoconfigure

.. uml:: 

    hide footbox
    RestTemplateAutoConfiguration -> RestTemplateBeanPostProcessor **  : otelRestTemplateBeanPostProcessor(ObjectProvider<OpenTelemetry> )
    -> RestTemplateBeanPostProcessor : postProcessAfterInitialization(RestTemplate, ..)
    RestTemplateBeanPostProcessor -> SpringWebTelemetry ** : create(openTelemetry)
    RestTemplateBeanPostProcessor -> SpringWebTelemetry :  newInterceptor()
    SpringWebTelemetry -> RestTemplateInterceptor ** : new RestTemplateInterceptor(instrumenter)

    RestTemplateBeanPostProcessor -> RestTemplateBeanPostProcessor  : addRestTemplateInterceptorIfNotPresent(restTemplate, interceptor);


.. List<ClientHttpRequestInterceptor> restTemplateInterceptors = restTemplate.getInterceptors();
    .. RestTemplateBeanPostProcessor -> restTemplateInterceptors.add(0, instrumentationInterceptor);


.. uml:: 

    hide footbox
    RestTemplateBeanPostProcessor -> SpringWebTelemetry ** : create(openTelemetry)
    SpringWebTelemetry -> SpringWebTelemetryBuilder ** : builder(OpenTelemetry)
    RestTemplateBeanPostProcessor -> SpringWebTelemetryBuilder : build()
    SpringWebTelemetryBuilder -> InstrumenterBuilder ** : Instrumenter.builder
    SpringWebTelemetryBuilder -> InstrumenterBuilder : setSpanStatusExtractor(HttpSpanStatusExtractor.create(httpAttributeGetter)
    InstrumenterBuilder -> Instrumenter ** : buildClientInstrumenter(HttpRequestSetter.INSTANCE)

    activate SpringWebTelemetry #LightSalmon
    -> SpringWebTelemetry : newInterceptor()
    SpringWebTelemetry -> RestTemplateInterceptor ** : RestTemplateInterceptor(instrumenter)
    deactivate 
    

.. uml:: 

    hide footbox
    InstrumenterBuilder -> InstrumenterBuilder : buildClientInstrumenter(TextMapSetter<REQUEST>)
    InstrumenterBuilder -> InstrumenterConstructor ** : propagatingToDownstream(requireNonNull(setter, "setter"))
    InstrumenterConstructor -> PropagatingToDownstreamInstrumenter ** 
    InstrumenterBuilder -> InstrumenterBuilder : buildInstrumenter(PropagatingToDownstreamInstrumenter, SpanKindExtractor.alwaysClient())

.. uml:: 

    interface OpenTelemetry 
    interface InstrumenterConstructor<RQ, RS>
    class PropagatingToDownstreamInstrumenter
    InstrumenterConstructor <|.. PropagatingToDownstreamInstrumenter
    class PropagatingFromUpstreamInstrumenter
    InstrumenterConstructor <|.. PropagatingFromUpstreamInstrumenter


From upstream

.. uml:: 

    hide footbox
    Spring -> SpringWebMvcTelemetry ** : create(openTelemetry)
    SpringWebMvcTelemetry -> SpringWebMvcTelemetryBuilder ** : builder(OpenTelemetry)
    SpringWebMvcTelemetry -> SpringWebMvcTelemetry : build()
    SpringWebTelemetryBuilder -> InstrumenterBuilder ** : Instrumenter.builder
    SpringWebTelemetryBuilder -> InstrumenterBuilder : setSpanStatusExtractor(HttpSpanStatusExtractor.create(httpAttributeGetter)
    InstrumenterBuilder -> Instrumenter ** : buildServerInstrumenter(JavaxHttpServletRequestGetter.INSTANCE)

    SpringWebMvcTelemetry -> SpringWebMvcTelemetry : createServletFilter()
    SpringWebMvcTelemetry -> WebMvcTelemetryProducingFilter **  : new WebMvcTelemetryProducingFilter(instrumenter)

.. uml:: 

    hide footbox
    InstrumenterBuilder -> InstrumenterBuilder : buildServerInstrumenter(TextMapGetter<REQUEST>)
    InstrumenterBuilder -> InstrumenterConstructor : propagatingFromUpstream(requireNonNull(getter, "getter"))
    InstrumenterConstructor -> PropagatingFromUpstreamInstrumenter ** 
    InstrumenterBuilder -> InstrumenterBuilder : buildInstrumenter(PropagatingFromUpstream, SpanKindExtractor.alwaysServer())

.. uml:: 

    hide footbox
    -> PropagatingFromUpstreamInstrumenter : start(Context parentContext, REQUEST request)
    PropagatingFromUpstreamInstrumenter -> ContextPropagators : getTextMapPropagator()
    ContextPropagators -> TextMapPropagator **
    PropagatingFromUpstreamInstrumenter -> TextMapPropagator : extract(parentContext, request, getter)
    PropagatingFromUpstreamInstrumenter -> Instrumenter : start(Context parentContext, REQUEST request)

