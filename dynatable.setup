$(document.body).on('dynatable:init', '#dynatable', function (e, dynatable) {
    $('.dynatable-search')
            .wrapAll('<div id="dynatable-header" class="row m-b-sm"><div class="col-md-12"/></div>');

    $('.dynatable-record-count, .dynatable-paginate')
            .wrapAll('<div id="dynatable-footer" class="footer m-t-lg"/>');

    $('.dynatable-search')
            .addClass('col-md-2 pull-right');

    $('.dynatable-search')
            .find('input')
            .addClass('form-control input-sm')
            .attr('placeholder', 'Buscar');
});

$(document).on('dynatable:afterUpdate', '#dynatable', function (e, dynatable) {
    $('.dynatable-paginate li').first().remove();
});

$(document).on('dynatable:ajax:error', '#dynatable', function (e, dynatable) {
    var error = "Error al conectar al backend: "
            + dynatable.xhr.status
            + " - "
            + dynatable.xhr.statusText;

    $(this).html('<div class="alert alert-warning"><h4>' + error);
    $('#dynatable-footer, #dynatable-header').remove();
});

$.dynatableSetup({
    inputs: {
        searchText: '',
        paginationClass: 'pagination dynatable-paginate pull-right',
        paginationActiveClass: 'active',
        paginationDisabledClass: 'disabled',
        paginationPrev: 'Anterior',
        paginationNext: 'Siguiente',
        recordCountPageBoundTemplate: '{pageLowerBound} al {pageUpperBound} de',
        recordCountPageUnboundedTemplate: '{recordsShown} de',
        recordCountTotalTemplate: '{recordsQueryCount}',
        recordCountFilteredTemplate: ' (Filtrados de un total de {recordsTotal} registros)',
        recordCountText: '',
        recordCountTextTemplate: '{text} {pageTemplate} {totalTemplate} {filteredTemplate}',
        processingText: 'Cargando Información <i class="fa fa-spinner fa-spin fa-pulse"/>'
    },
    features: {
        sort: false,
        perPageSelect: false
    },
    params: {
        records: 'data',
        totalRecordCount: 'total',
        queryRecordCount: 'filtered'
    },
    dataset: {
        ajax: true,
        ajaxOnLoad: true,
        ajaxDataType: 'json',
        ajaxMethod: 'POST',
        records: [],
        perPageDefault: 10
    },
    table: {
        bodyRowSelector: 'div'
    }
});
